---
title: "How can I get my joystick to work in gameport?"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by mikaelstaldal on 2006-08-17
I have a ASUS A8V-E Deluxe motherboard with built-in analog gameport. To that gameport I have connected my Logitech Wingman Extreme Digital joystick (which is an analog joystick, dispite its name).

How can I get this to work in Ubuntu (6.06)? I have heard that the joystick is accessed on /dev/input/js0 (or is it /dev/js0?), but there are no such devices on my system.

The gameport is enabled in BIOS Setup.

When I do lsmod, I get this line:
gameport               15496  2 snd_via82xx,analog

---

### Post by jsandys on 2006-10-13
Same question at this thread:
[http://ubuntuforums.org/showthread.php?p=1614638](http://ubuntuforums.org/showthread.php?p=1614638)

---

### Post by nalmeth on 2006-10-13
I have the same joystick, and even after following steps outlined by other users, can't get the thing going. I kind of gave up after a while, maybe it's worth looking at again.

---

### Post by AR_Kozz on 2006-10-21
I am also trying to figure this out.  It is kind of annoying that the officia l documentation says absolutely nothing about gameports and how to get them to work. 

  I too found that dev/js0 was absent.  After reading 'info MAKEDEV' I ran the command MAKEDEV js and there was still no js device listed... until I ran a find that located it in a hidden folder called '.static'

  Just what the .static folder is, I am now trying to find out, but the js0 device in there doesn't work with jstest, jscalibrator, or any of the others when I enter the command line.

---

