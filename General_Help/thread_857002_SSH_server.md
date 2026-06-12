---
title: "SSH server"
date: 2008-07-12
forum: General Help
---

### Post by aidy12 on 2008-07-12
Hi, I recently got a VPN to host a game server on, I got it compiled alright, and I can run it on the SSH client using "./server", which brings up the server information, but when I close the SSH client, the server closes also.
Am I doing something wrong, because I thought the program was supposed to stay open:confused:.
Thanks, Aidan

---

### Post by txcrackers on 2008-07-12
To duplicate what you're doing via SSH:
```
nohup ./server &
```
*&* puts the server process in the background
*nohup* "disconnects" the server process from your terminal

However, you should also think about starting the server via an "init" script - which, when properly installed, will automatically start/stop the server when the computer starts/stops. The current scripts used are in /etc/init.d - you can study those to figure out how to create one for your server.

There are also .deb packages for VPN servers that takes care of all this stuff for you...

---

### Post by aidy12 on 2008-07-12
Awesome, thanks for your help. I was searching for ages and couldn't find anything that worked, but that command worked perfectly.
Aidan

---

