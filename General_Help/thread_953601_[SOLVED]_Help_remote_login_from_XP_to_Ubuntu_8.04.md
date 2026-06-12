---
title: "[SOLVED] Help remote login from XP to Ubuntu 8.04"
date: 2008-10-20
forum: General Help
---

### Post by carfinder01 on 2008-10-20
Hey I have been researching online from a way i can log into my home ubuntu box from my xp machine. 
I know i can use putty and ssh but i will only be able to run in the terminal. I looked into vnc and it only let me do remote control. Any one know how i can configure my ubuntu box so i can log in from windows same way  as windows rdc works? I want to be able to view the gnome desktop so i can use all my applications as well as run the terminal. I would really appreciate any help.:(

---

### Post by pedro_orange on 2008-10-20
You should be able to remote desktop to your Ubuntu box from Windows with VNC, if you install VNC on your Ubuntu desktop and the VNC client on the Windows machine.

You may have problems if you're trying to connect through a firewall.

---

### Post by carfinder01 on 2008-10-20
From my understanding VNC will only do remote control where you control the current desktop. And when i set it up thats exactky what happened i was controlled the screen. I would like to be able to log into a new session

---

### Post by bodhi.zazen on 2008-10-20
You can do this with an alternate VNC server. vnc4server or FreeNX.

---

### Post by carfinder01 on 2008-10-23
Hey guys
Thanks for all the suggestions i found a how to that was not too hard to follow and it worked fine using vncviewer and ssh using putty on XP and vnc4server for linux
[http://backports.ubuntuforums.com/showthread.php?t=795036](http://backports.ubuntuforums.com/showthread.php?t=795036)

---

