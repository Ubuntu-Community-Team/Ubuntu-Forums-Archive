---
title: "Need help Updating to 9.04 from terminal"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by kakarotman on 2009-05-04
So i was using virtualbox and i could not get the mouse out of windows xp so i force turned off my laptop and when i turned it back on both the mouse and keyboard were not responding at all. I restarted and tried several times with no luck.

So i want to try and update from the terminal so i need these commands:

how to connect to my wireless network
how to update to version 9.04

Also if you know how to fix my computer lockup problem let me know!

---

### Post by Zorael on 2009-05-06
Forced shutdowns are bad for you. Use [SysRq commands](http://kember.net/articles/231/reisub-the-gentle-linux-restart[/url) if you really need to reboot when X isn't responding.

If your keyboard and/or your mouse isn't working in X, I'd try reconfiguring HAL.
```
$ sudo dpkg-reconfigure hal
```
As for connecting to a wireless network via a terminal, the command you need to use is [iwconfig](http://linux.die.net/man/8/iwconfig). For instance, this is the command I use to connect to my old WEP-only router
```
$ sudo iwconfig *<device, wlan0>* essid *<essid>* key [1] *<first hex key>*
$ sudo dhclient wlan0
$ host ubuntu.com
```
As for upgrading via a terminal, I think you just need to edit your /etc/apt/sources.list file (and *.list files under /etc/apt/sources.list.d/) and replace all mentions of **intrepid** with **jaunty** in the lines that start with *deb* and *deb-src*. Then do a full-upgrade (or a dist-upgrade).
```
$ sudo aptitude update
$ sudo aptitude full-upgrade
```

---

