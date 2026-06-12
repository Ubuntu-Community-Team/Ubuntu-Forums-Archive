---
title: "Total Newbie here...  Need tons of help..."
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by 65Shelby on 2009-06-03
I just installed Ubuntu Server 9.04 and only have the command line working.  I am trying to get the GUI installed and working but I am not getting that done.
 
I need to install the GDM I guess?  But I am so new I dont even know how to change drives and change folders...
 
I am trying to install gnome and GDM but it keeps telling me it couldnt find the package.
 
Any help would be appreciated.
 
Shelby

---

### Post by lisati on 2009-06-03
The server edition disk doesn't normally install a GUI. You might want to try the following:
```
sudo aptitude install ubuntu-desktop
```
Note: it might need to download a lot of stuff so a good internet connection will be useful.

---

### Post by 65Shelby on 2009-06-03
I typed that in exactly and I get  "Couldn't find any package whose name or description matched "ubuntu-desktop"

---

### Post by ad_267 on 2009-06-03
Try a "sudo apt-get update" first, then try again.

It might be better to just start again and install the Ubuntu desktop edition if you haven't gone too far already and don't mind wasting some bandwidth. You can install all the server applications you need on the desktop version too.

---

### Post by 65Shelby on 2009-06-03
Ok DLing now... I have 22mb cable so I am good... Hmm already done, lets try...
 
 
Ok this is working, doing another DL now...
 
Thanks... I have a cheat sheet on  basic commands, is there another source for how to change Dirs, Drives, etc?  
 
I will need to gain remote access to other boxes and I have NO IDEA how to do that either.

---

### Post by zman58 on 2009-06-04
Install the desktop version. Ubuntu 9.04 desktop i386. You will find that it is the easiest to work with and learn from. It is also very stable and works best with the various hardware out there. The desktop version works great as a server too. If you are a newbie, then start with something easy and work your way up. I run a dedicated Ubuntu server, but would not recommend that to a newbie.

---

### Post by 65Shelby on 2009-06-04
Well I already had server installed... I got all the updates and installed the desktop and Gnome...
 
How do I utilize remote access/management from a desktop?  I will be installing Ubuntu desktop on my laptop today and will need to know how to remote into the servers

---

### Post by ad_267 on 2009-06-05
I think you can use Ubuntu's VNC client under Applications - Internet - Remote Desktop Viewer. I've only used this to control a session where another user is logged in already, but I think it's possible to use VNC to log in to a remote desktop by installing a VNC server on that machine. Someone else can hopefully explain this more.

Edit: This might help, although it's a bit old. I'd wait for someone else's advice to make sure this is still the way to go: [http://ubuntuforums.org/showthread.php?t=42941](http://ubuntuforums.org/showthread.php?t=42941)

---

