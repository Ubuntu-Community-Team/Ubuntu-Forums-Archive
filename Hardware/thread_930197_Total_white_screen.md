---
title: "Total white screen"
date: 2008-09-25
forum: Hardware
---

### Post by Solitus3989 on 2008-09-25
I recently installed ubuntu 8.04 and i am having some problems with it after I installed the updates.  I am running a Dell Inspiron 1520 with 2GB of ram, Nvidia 8600M gt, and an Intel dual core processor.  After turning on the restricted driver for my graphics card, I restart and ubuntu loads, i hear the login screen noise, but there is only a white screen with some lines.  I can type my login name and password and i will hear the login music, but the white screen never changes.

---

### Post by alan34 on 2008-09-26
Either when you get to the Grub Menu pick "recovery mode" (second line down) OR when you get to your white screen hit Ctrl-Alt-F2.


You should now have a black screen with a login prompt. Login then type

sudo dpkg-reconfigure -phigh xserver-xorg

and then type

sudo shutdown -r now

The first command will rewrite your /etc/X11/xorg.conf file to use a "safe" video driver and the second command just restarts your computer. All being well you should have a usable desktop back but no compiz etc (sorry), but you can try the restricted driver again now you know how to fix it 
:)

Good luck


Look here seems you are not the only one!

[http://ge.ubuntuforums.com/showthread.php?t=712479](http://ge.ubuntuforums.com/showthread.php?t=712479)

---

### Post by Solitus3989 on 2008-09-27
Yep, I did ran it in recovery mode and it reconfigured my .xorg file so I can at least use it.  Ive tried using EnvyNG, manual driver installs, restricted drivers install, Nvidia binaries, but still same old white screen.  Oh well, no compiz until they hopefully come out with an update fix for this.  Thanks though!

---

