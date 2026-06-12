---
title: "Server UI"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by bikingbadger on 2009-02-15
Hi all,
As a completely nebt to the world of Linux/Unix I decided to go with Ubuntu. As a born and bred South African I reckon a bit of patriotism came into the equation in using Ubuntu but mostly because I have heard that it is the easier platform to get your hands dirty with. My idea is to set up a file server and also a server that I can test my Java Applications on. I received the 8.10 Server Edition in the mail and went about the easy installation process. After get logged in I understood from the forums that there is no root user. What I would like to know though is about the UI. Does the server edition not come bundled with the UI? If it does can someone please help me understanding how to get it running. I may be in over my head but hopefully you can help me inflate my water wings till I find shallower water.

---

### Post by Sorivenul on 2009-02-15
The Server Edition does not come bundled with a GUI, but one is easily installable. If you want the default Ubuntu GUI:
```
sudo apt-get install ubuntu-desktop
```
This will ask you to enter your password (it is the one you gave your user during installation, the same one you use to log in); it will then install all the packages in the typical Ubuntu install. 

That is the quick way, and it leaves you with a lot of "bloat" or unnecessary packages that will slow down your server, which is part of why the server comes without a GUI. There are much more minimal setups if you still want a GUI to help with your server.

EDIT:
Just for further explanation...
The command used to install the entire Ubuntu desktop is prefixed with "sudo". "sudo" is how a normal user can act as root in an Ubuntu system. Look at the community documentation on [Root/Sudo]("https://help.ubuntu.com/community/RootSudo") for more information.

I run a few small servers myself, and if I need a GUI I use ion2 or ion3 (these are window managers as opposed to the GNOME/KDE/Xfce desktop environments). When I started with servers I used Fluxbox or Openbox, which are a bit easier to understand, but still very lightweight. There is some excellent community documentation regarding Openbox (now often coupled with LXDE (a lightweight desktop with a menu bar) that I will try to find a link to if another user does not beat me to it.

EDIT x2:
[urukrama's Openbox guide for Ubuntu]("http://urukrama.wordpress.com/openbox-guide/")
[Community documentation on Openbox]("https://help.ubuntu.com/community/Openbox")
[UbuntuGeek tutorial on LXDE]("http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html")
[LXDE setup instructions from the LXDE project]("http://lxde.sourceforge.net/install.html")

---

