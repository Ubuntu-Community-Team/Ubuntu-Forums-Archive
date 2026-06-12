---
title: "I want to install an intel video driver but terminal doesn't work"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by somewherecheap on 2009-07-22
Hello,
          I've just installed Ubuntu 9.04 on an old PC, when I try to use it there is a terrible lag when I move the mouse. I read on a website that I should type sudo apt-get install xserver-xorg-video-intel in terminal to install driver's but when I click on terminal there is just a blank white block. How can I resolve this?

There is a picture of my desktop.

Thanks,

---

### Post by Mark Phelps on 2009-07-22
You need to exit XWindows and run a "console" by entering Ctl-Alt-F2.  That will kill the desktop and put you at a command line.  When you're done using commands, you can restart, or press Ctl-Alt-F7 to restart the XServer.

---

### Post by ajgreeny on 2009-07-22
Ctrl+Alt+F2 will not stop the x-server, I'm afraid, but just switch you to one of the 6 cli terminals available, leaving x still open.  To stop x you will need to use the command from the Ctrl+Alt+F2 console ```
sudo /etc/init.d/gdm stop
```then do the intel driver install and then ```
sudo /etc/init.d/gdm start
```to restart the x-session.  If nothing happens after that final command just type *startx*.

---

### Post by somewherecheap on 2009-07-23
I've resolved the problem

---

