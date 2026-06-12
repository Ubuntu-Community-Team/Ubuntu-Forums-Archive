---
title: "server start up text mode help confused"
date: 2008-09-21
forum: General Help
---

### Post by lahp on 2008-09-21
ok i have installed the server edition cause thts what i want a server i am currently running it on my test machine...  all i get is the user@ubuntu:~$ 
what do i do is there any possible way i can get graphical display without internet connection updates?

---

### Post by strider1551 on 2008-09-22
You don't have a graphical display because servers are typically command-line only.  This is the accepted norm.  If you are trying to learn how to manage a server for common things such as http, I recommend you push yourself to learn how to do things from just the command-line.

That being said, it looks like you are asking how to install gnome without internet access.  It's possible, but I imagine it will be a pain.  These links ([one]("http://ubuntuforums.org/showthread.php?t=186298"), [two]("http://stevenroddis.com/2007/01/09/install-gnome-on-ubuntu-server/index.html")) describe how to install gnome if you had internet.  Without internet, you will either have to get the packages manually and put them on a thumbdrive or whatnot, or get a live-cd and add it to your sources list.

It will be far easier to either (a) temporarily connect the machine to a network or (b) reinstall a desktop version.

Last side note:  it seems curious that you want a server with no internet access.  What are you planning on doing with it?  I suppose it could just be for a local network with no internet...

---

