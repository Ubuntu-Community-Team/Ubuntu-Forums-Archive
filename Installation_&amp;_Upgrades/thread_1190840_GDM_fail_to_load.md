---
title: "GDM fail to load"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by LlirasChosen on 2009-06-18
Hey guys, I can't log into a standard session desktop manager, both GDM and now KDE since I had just installed that.  My issues started a few days ago when I tried to hook up a secondary monitor.  Since Gnome didn't auto configure my secondary monitor I started looking for a program to install to get a decent dual head configuration up and running.  I couldn't find anything, might be due to me using an ATI card.  But I found a lot of Xorg.conf pages, and then I found this code and my problems started on reboot.```
aticonfig --initial=dual-head
```So now that youu have the background the things I have tried are:
```

apt-get remove --purge xorg-driver-fglrx

apt-get remove ubuntu-desktop && apt-get autoremove && apt-get autoclean && apt-get install ubuntu-desktop

apt-get --reinstall ubuntu-desktop

sudo dpkg -reconfigure -phigh xserver-xorg

sudo dpkg-reconfigure xserver-xorg

```I've now been able to log into my machine and don't get locked out at a scrambled screen.  However all I can log into are the failsafe terminal and failsafe gnome sessions.  Any ideas?

I'll also post mt current .xsessions-errors log.

> /etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator
Failed to contact the GConf daemon; exiting.--LlirasChosen

---

