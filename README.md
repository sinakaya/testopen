# OpenConnect-VPN-Server
**2022 OCT UPDATE**: We dockerized and added Dockerfile to run it anywhere you want on any linux distro easily.
Buggy script for configuring OpenConnect (ocserv) protocol on the server easily and automatically.
## Script Installation
Tested on ubuntu 18.04 and 16.04.

Download and saving script on your server:
```bash
curl -O https://raw.githubusercontent.com/iw4p/OpenConnect-Cisco-AnyConnect-VPN-Server-OneKey-ocserv/master/ocserv-install.sh
```

Making script executable
```bash
chmod +x ocserv-install.sh
```

And then just run it:
```sh
./ocserv-install.sh
``` 
or
```sh
sudo bash ocserv-install.sh
``` 

## Docker Installation
1. Install Docker
2. Build docker image
```bash
docker build -t twouserserver https://github.com/sinakaya/openconnecttwouser.git#main
```

3. Run docker container
```bash
docker run --name twouserserver --privileged -p 443:443 -p 443:443/udp -d twouserserver
```

4. Add user
```bash
docker exec -ti twouserserver ocpasswd -c /etc/ocserv/ocpasswd testUserName
```

5. Change user password
```bash
docker exec -ti twouserserver ocpasswd -c /etc/ocserv/ocpasswd testUserName
```

6. Delete user
```bash
docker exec -ti twouserserver ocpasswd -c /etc/ocserv/ocpasswd -d testUserName
```

7. Lock user
```bash
docker exec -ti twouserserver ocpasswd -c /etc/ocserv/ocpasswd -l testUserName
```

8. Unlock user
```bash
docker exec -ti twouserserver ocpasswd -c /etc/ocserv/ocpasswd -u testUserName
```

9. Show all users and their hashed password
```bash
docker exec -ti twouserserver cat /etc/ocserv/ocpasswd
```

## Features
- Easy install
- Easy uninstall
- Add User
- Change Password
- Show All Users
- Delete User
- Lock User
- Unlock User

## How to connect to it?
For making connection to your server, you can use `AnyConnect`, `OpenConnect` or other alternative clients.

- AnyConnect: [GUI AnyConnect client for available platforms](https://it.umn.edu/vpn-downloads-guides).
- OpenConnect: [OpenConnect client for Linux](https://computingforgeeks.com/how-to-connect-to-vpn-server-with-openconnect-ssl-vpn-client-on-linux/).

And one more thing, contributions are welcome.

## More
The script is based on [here](https://ocserv.gitlab.io/www/recipes-ocserv-configuration-basic.html)
