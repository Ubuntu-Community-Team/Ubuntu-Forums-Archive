---
title: "Switching back to default graphics driver"
date: 2013-11-27
forum: Hardware
---

### Post by tmty-vdl on 2013-11-27
Hello

I am using Xubuntu 13.10, and have been using the fglrx-updates driver for quite some time now.

Alas, it seems that it might have caused damage of some kind, as when I try to switch back to the xorg drivers, there's horrible graphical distortion after I log in.

I have tried sudo amdconfig --initial, which doesn't work as amdconfig isn't a recognized command. I have done sudo dpkg-reconfigure xserver-xorg, which doesn't help.

As best as I can tell, the graphical distortion that appears (and which is the only thing I see), is a distorted version of what was on my screen before I restarted the computer, so the problem could have something to do with the memory.

I'm apologize for my English, as it isn't my native language, and I would be very grateful for any assistance that can be offered.

EDIT: I tried taking a screenshot while the screen was distorted, but it isn't showing up on my hard drive, although ctrl + alt + F6 did wrk (which is how I managed to reinstall fglrx-updates and reboot).

---

### Post by Mark Phelps on 2013-11-28
See the link on how to purge the fglrx drivers:  [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx")

---

