---
title: "Fresh install, issue with VNC"
date: 2008-08-24
forum: General Help
---

### Post by CapinPete on 2008-08-24
Due to my issues, I can understand why linux hasn't exactly made as much progress as we all know it can.  Anyway, I digress.

I just installed Ubuntu 8.04.  On the first reboot I enabled remote desktop connections.  I went upstairs, logged in with VNC and did a few things including installing all the updates.  Rebooted.  Now, I can't connect with VNC.  WTF?  I did an ssh -X session and ran vino-preferences.  Everything seems to be intact.  I have removed apparmor and disabled the ubuntu firewall.  All other services on this box work including ssh and swat.

---

### Post by qstraza on 2008-08-24
well first off go to ubuntu pc and check if vnc server is listening on any port.

```
sudo lsof -i:port
```
change port with your vncs port number, default is 5900, you can use a range like 1-65535.

If it is not listening, rerun it. If it is listening, type in this command to see if it is working
```
telnet localhost port_of_vnc
```
if it doesnt work, try rerunning vnc server

If it works (than only question is your network and firewall), than try doing
```
telnet ip_of_ubuntu port_of_vnc
```
from other computer, if it works, than your vnc server is working, if not, there is something with network, firefox or something.

when telneting you will see something simular to this
```
q@lj:~$ telnet localhost 65002
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
RFB 003.008
```
this is good,

bad is if you get connection refused or no respose at all.

---

### Post by CapinPete on 2008-08-24
```
# lsof -i:5900
COMMAND    PID USER   FD   TYPE DEVICE SIZE NODE NAME
dbus-daem 5809 root   16u  IPv6  17119       TCP *:5900 (LISTEN)

```

I ran the first command and that's what I got.  It seems something is listening on that port but it doesn't appear to have anything to do with VNC.

---

### Post by qstraza on 2008-08-24
if vnc wants to listen on 5900, that can be a problem. Since 5900 is already taken. So configure your vnc to listen on 5901 instead.

---

### Post by CapinPete on 2008-08-24
This is so frustrating.  I did a fresh install and it was working on the first boot.  I just updated all my packages and now it doesn't work.  This is worse than when Microsoft breaks something with Windows Update.  At least then the issue is usually well documented within hours.

---

### Post by qstraza on 2008-08-24
well, does it work now? ;)

---

### Post by CapinPete on 2008-08-24
No, it's not working at all.  I just purged vino and I'm going to try setting up another VNC server.

---

### Post by qstraza on 2008-08-24
try this
```
 sudo apt-get install x11vnc
```

for running it run
```
x11vnc -rfbport port_number -display :0 -shared -many -passwd password -bg

```

-bg stands for background, maybe you should run it w/o -bg option, until you set everything up right ;)

---

