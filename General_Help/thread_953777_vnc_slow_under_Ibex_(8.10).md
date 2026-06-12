---
title: "vnc slow under Ibex (8.10)"
date: 2008-10-20
forum: General Help
---

### Post by apastuszak on 2008-10-20
I just upgraded to 8.10 a few days ago, and am current on all updates through this morning.

When I connect to my workstation via VNC from work, it's WAY slower than it was under 8.04.  Has anyone else seen this. or know of a way to speed things up?

Andy

---

### Post by oalonso on 2008-11-06
I just upgraded to Ubuntu 8.10 and the VNC server is much slower than the previous 8.04 release. :(

---

### Post by cperrin88 on 2008-11-10
The same here. Has anyone an idea how to fix this?

---

### Post by mocha on 2008-11-17
I have the same problem.  It's very strange, I keep looking for options that might have changed.  It "visually" appears that no compression is being applied to the connection.  The photo on my desktop for example is full res, under Hardy the VNC connection seemed to self-adjust the compression levels based on the available bandwidth.  Photos would look compressed for example, I'm not seeing any of this on Intrepid, it's trying to make the connection like I'm no another computer on the LAN.

---

### Post by myxiplx on 2008-11-28
Just hit the exact same thing.  Can't see any compression being applied and it's unusably slow.  Connecting to a 2048x1024 screen remotely is just painful when you can see it being redrawn a line at a time.

---

### Post by sebos69 on 2008-12-14
yep, same problem here...

a bug was reported here:
[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/299112](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/299112)

---

### Post by MystaMax on 2008-12-21
I'm having the same problem. Connecting to PCs on the same LAN (running ubuntu 8.10) is incredibly slow! Completely unusable. 

I thought about using an alternative, [FreeNX]("https://help.ubuntu.com/community/FreeNX"), but I don't think it allows you to connect to a users session already in progress.

---

### Post by rcolson9333 on 2009-01-19
same prob. would really like an explanation or solution.

---

### Post by Peter09 on 2009-01-19
FreeNX will allow you to connect to a session already in progress, I believe its call shadowing.

---

### Post by Mordy2009 on 2009-03-26
I just installed it and have been wasting hours trying to determine why Windows XP using VNC to Ubuntu is unbearably slow. Also wondering why so many people have been asking the same thing without good replies. Any info on how to PROPERLY install and operate a remote desktop application in Ubuntu would be appreciated as it seems the built in one jut does not have what it takes to be functional. Please help, Im a new user and need this...

---

### Post by helleman on 2009-06-11
I have disabled the remote desktop sharing so that I can use x11vnc which allows me to see the login screen through vnc , which means on a reboot or power outage I can still  connect to my ubuntu box.


to do this, you can use vino-server or  x11vnc.


 I have also found that to speed up ultra slow connections , for my hardware I needed to use the -noxdamage flag. I found this out by monitoring the vnc log file as created by x11vnc :


 I used in /etc/gdm/Init/Default :


 /usr/bin/x11vnc -rfbauth $home/.vnc/vncpasswd -o /var/log/x11vnc.log -noxdamage -forever -bg


 ( you can set your password by using vncpasswd ) - if you don’t want a password, skip the -rfbauth vncpasswd switch.


to see the full instructions on how to configure remote login, see this link:


[http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu](http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu)

---

