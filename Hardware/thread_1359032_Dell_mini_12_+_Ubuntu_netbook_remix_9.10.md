---
title: "Dell mini 12 + Ubuntu netbook remix 9.10"
date: 2009-12-19
forum: Hardware
---

### Post by e-gandalf on 2009-12-19
I just installed ubuntu netboox remix on dell mini 12.

The experience was OK, I just had to install broadcom STA driver to get it working.

One thing that was really unacceptable, was graphics. It was super slow. I found out that it runs vesa by default and tried to install Poulsbo driver, first from:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)
and then upgraded to:
[http://gadgetmix.com/index/new-gma-500-poulsbo-drivers-for-the-ubuntu-9-10-karmic-koala/](http://gadgetmix.com/index/new-gma-500-poulsbo-drivers-for-the-ubuntu-9-10-karmic-koala/)

now, the 2d seems to work a bit faster, but I cannot get compiz running (I whitelisted it) with error:

gandalf@gandalf-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

and all glxinfo, glxgears give:

gandalf@gandalf-laptop:~$ glxinfo
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

Anyone has any experience with this?

---

### Post by e-gandalf on 2009-12-19
ok, after another hour, I reverted to the jaunty drivers and things started working.

Now, unfortunately the compiz leaves ugly artifacts all around whenever I switch windows.

---

### Post by didi2005 on 2009-12-19
Found out that desktop version is better than remix...
My Dell mini 12, after installing 9.10, found audio and webcam problem. Did u having such issue also?

---

