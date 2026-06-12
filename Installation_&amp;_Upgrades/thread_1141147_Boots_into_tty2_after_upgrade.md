---
title: "Boots into tty2 after upgrade"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by aaronwinborn on 2009-04-28
This is a new thread from [http://ubuntuforums.org/showthread.php?p=7167096#post7167096](http://ubuntuforums.org/showthread.php?p=7167096#post7167096) where I'm trying to fix a dead black screen after upgrading from hardy heron.

I boot into tty2 every time I restart the computer now, even when restoring old xorg.conf backup files. I have to hit ctrl-alt-f7 to access the (still dead) xserver kdm screen. Anyone know how I can fix that little problem?

The only thing I've done beyond upgrading is to run dpkg-reconfigure -phigh xserver-xorg. But even restoring the resulting backup xorg.conf.[date-time] file doesn't resolve the issue.

Thanks,
Aaron

---

### Post by aaronwinborn on 2009-04-28
or rather, it's tty1.

and ctrl-alt-f7 doesn't actually do anything.

if i run startx, then the screen turns black, and there's no other response (including from ctrl-alt-fn)

---

### Post by aaronwinborn on 2009-04-28
spoke too soon.

running startx freezes it for a bit, before going to a black screen. after that, ctrl-alt-fn works.

going back to tty1, i see the following error:

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System:....
....
(==) Log file: "/var/log/Xorg.0.log", Time...
(==) Using config file: "/etc.X11/xorg.conf"
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

---

### Post by Monsieur Gonzalez on 2009-04-28
Well, it certainly looks like a graphics driver problem. Here's what I'd do :

1- from the command line, install envyng-core. You might find more info about it [here]("http://albertomilone.com/nvidia_scripts1.html"). 

2- sudo envyng -t 

3 - Select the driver for the card.

4- Reboot

I've found some problems with graphic cards drivers when upgrading (not from 8.10 to 9.04, everything went fine), and envyng removed whatever was left of the old nvidia install and installed the new driver.

Good luck.

---

