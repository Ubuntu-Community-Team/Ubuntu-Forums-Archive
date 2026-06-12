---
title: "Remote Desktop Viewer"
date: 2008-11-16
forum: General Help
---

### Post by ajsup on 2008-11-16
Dear all,

I am in Bangkok, Thailand using ubuntu 8.04
I want to connect to a friends laptop (chennai, India) with ubuntu 7.10 using Remote Desktop Viewer.. WE some how cannot. I tried here with another computer and i could.. kindly let me know wat the problem is.. Thanks..

---

### Post by Chesamo on 2009-03-18
(Sorry for the massive bump, but it looks like a topic that needs to be answered)

You have to have your friend forward their port in order to Remote Desktop/VNC into their computer. It seems like your port is already forwarded.

VNC uses port 5900. You can check out [http://portforward.com/](http://portforward.com/) for details on how to forward ports on different routers.

---

### Post by fieroboom on 2009-03-19
In order to keep the solution simple, secure, and keep it Ubuntu, it might be easier to just do it with a reverse ssh tunnel. Your friend will need to be able to ssh to your machine, so you might need to add them as a user, and make sure port 22 is forwarded to your machine if you're behind a router.
Here's how I'd do it:
```
sudo adduser <friends_username>
```
It'll ask you to give that user a passwd, so go ahead and do that, and then you can just press enter through the rest of the dialogue if you want.
Then, have your friend run these commands:
```
sudo apt-get install x11vnc

x11vnc -quiet -shared -forever /home/<username>/.Xauthority -display :0

ssh -nNTR 5900:localhost:5900 your.ip.address

```
After that, you just connect like this:
```
vncviewer localhost
```

This is probably the best solution, because you're tunneling vnc through a secure ssh tunnel. VNC on it's own isn't very secure, and port forwarding in routers is kinda out of the scope of support here.
Let me know if I can help any more!
:D
-Paul

---

