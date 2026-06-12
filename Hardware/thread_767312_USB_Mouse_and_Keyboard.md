---
title: "USB Mouse and Keyboard"
date: 2008-04-25
forum: Hardware
---

### Post by SirThom on 2008-04-25
I wanted to post this to absolute beginners because it sounds like such a n00bish question, but the forums won't let me so I'm posting here.

I did a fresh install of Heron on my HP Pavillion TX 1000 nr and just finished getting broadcom wireless working.  nvidia comes later.

Now when I set it up I had an external USB mouse and keyboard plugged in.  When I set up the WiFi I had to carry my laptop into another room to get to the wired LAN, and now that I'm done I bring it back and discover that my USB mouse and keyboard are not recognized.  What gives?  I tried rebooting, disconnecting and reconnecting them, and neither works.  Can somebody help me?

I got the WiFi working with the instructions here: [http://ubuntuforums.org/showthread.php?t=751054](http://ubuntuforums.org/showthread.php?t=751054) .  There was no line in */etc/udev/rules.d/70-persistent-net.rules* that said *SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:12:17:b6:8d:e5", NAME="eth2"*, so instead I added the line that I was meant to replace it with as an additional line.

Here is my current */etc/udev/rules.d/70-persistent-net.rules*:

thom@Archimedes:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:24:18:1e:ab", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4311 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:73:3f:d1:72", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# new one thom adds
SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="00:12:17:b6:8d:e5", ATTR{type}=="1", NAME="eth2"

thanks.

**<edit> Nevermind, I got is sorted.  Ndiswrapper apparently has a reputation for hijacking USB ports.  Even though I'm not using ndiswrapper now, I did install it initially to ger broadcom working, and even after I deleted it the ports were still disabled.  I hadn't done enough to my system yet that doing a clean install to fix that was a big deal.</edit>**

---

### Post by alex sun on 2008-05-21
Hi, everyone!
What if I need both wireless and USB mouse?

It worked in Gusty, but it doesn't in Hardy.

Help please...

---

### Post by SirThom on 2008-06-10
I have switched to xubuntu, and I have noticed that my usb keyboard works if I boot with it plugged in, but if I try to plug it in after booting, or unplug it and plug it back in then it doesn't work.  It's quite mysterious.

---

### Post by benoy4007 on 2008-06-11
set device event in xorg.conf

---

### Post by SirThom on 2008-06-14
> **benoy4007 said:**
> set device event in xorg.conf

Looking through my ubuntu book and google I can't figure out how to do that?

---

### Post by SirThom on 2008-07-01
bump
Does anyone know how to do this?  It's really annoying to reboot every time I plug in a usb device.

---

### Post by AndrewTheArt on 2008-07-18
I have the same issue ... if anyone has any ideas, please help us out!

---

### Post by lisati on 2008-07-18
USB keyboards & mice are occasionally problematical. The solution I found through these forums for what _***might***_ be a variation of this can be found at [http://ubuntuforums.org/showthread.php?t=854684](http://ubuntuforums.org/showthread.php?t=854684)

EDIT: Although the problem I experienced wasn't exactly the same, I offer the solution in the hope that it might be a place to start.

---

