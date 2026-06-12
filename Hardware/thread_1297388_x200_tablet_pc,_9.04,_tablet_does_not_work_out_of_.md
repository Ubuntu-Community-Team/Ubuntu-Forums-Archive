---
title: "x200 tablet pc, 9.04, tablet does not work out of the box"
date: 2009-10-21
forum: Hardware
---

### Post by hcdaume3 on 2009-10-21
Hi all --

I was really excited when I saw everyone posting that their x200 tablet worked out of the box with ubuntu 9.04.  Sadly, that's not happening for me!  It's not happening in live mode, and it's not happening in installed mode.

I've done a bunch of investigating, but nothing seems to work.

1) I tried editing xorg.conf as per 8.10.  This just causes the machine to hang on boot.

2) If I 'cat /proc/bus/input/devices', there's nothing listed that looks like the wacom serial table.

3) If I run 'hal-device', there's nothing there that looks like the tablet.

4) 'xinput --list' doesn't show up anything.

5) hal-find-by-property can't find anything with wacom.

Basically, it looks like as far as the machine is concerned, there's no tablet hardware.  If I look in /var/log/Xorg.0.log, there's nothing about wacom either.

And yes, if I boot into windows, it works fine: it's not that the machine is broken.

Everything else on the thinkpad x200 works fine, except for this.  Please please help!!!

 - hal

---

