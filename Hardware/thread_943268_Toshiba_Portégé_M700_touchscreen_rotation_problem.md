---
title: "Toshiba Portégé M700 touchscreen rotation problem"
date: 2008-10-10
forum: Hardware
---

### Post by willmcgree on 2008-10-10
Hello everyone.

I picked up a Toshiba M700 hybrid tablet this week and almost everything is working (including pen input and screen rotation). I can even use the pen in portrait mode, but the same cannot be said for the finger-driven touchscreen.

As far as I can tell, the calibration is correct for the top-right of the screen, but it's as though every movement is being scaled to fit a landscape desktop on a portrait screen.

I have modified my xorg.conf file as the Laptop Testing Team recommends and my finger touchscreen does in fact work as required in both normal and 180 degree rotation.

Please help me guys. I know there's probably something simple I've missed, but I can't find any documentation about it anywhere.

Thanks,
Will

Oh, and if anyone can explain why the madman2k PPA doesn't have the fprint packages any more, that would be great. :)

---

### Post by 1supa1 on 2008-12-04
I have the exact same rotation problem. It seems like the pen is configured properly only for the landscape mode.

---

### Post by Favux on 2008-12-07
Hi willmcgree,

Have you calibrated touch?  Open a terminal and type "wacomcpl" and the wacom calibration gui will open.


1sups1,

I don't think you have the same problem as willmcgree.  If your stylus (pen) isn't reorienting into portrait mode when you rotate the screen then wacom doesn't recognize it should be reorienting the stylus.  Is your stylus configured through HAL or through xorg.conf?  Say you rotate the screen right using:
```
   xrandr -o right

```
to tell wacom to rotate the stylus you need:
```
   xsetwacom set "stylus" Rotate CW
```
Or there are some daemon's that will do the same thing.  For instance Tom Jaeger's wacomrotate daemon.

To get a general idea of what I'm talking about you could check out:
   [http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

Hope this helps.

---

### Post by Favux on 2008-12-20
Hi 

Your problem is reported at Launchpad here:

 [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/300980]("https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/300980")
Apparently it is a bug in linuxwacom utilities.

The solution is to compile and use the latest linuxwacom driver 0.8.2 at the Linux Wacom Project.  It has the patch that fixes the bug.  This wiki tells you how:

  [https://help.ubuntu.com/community/Wacom/LatestDriver]("https://help.ubuntu.com/community/Wacom/LatestDriver")

I hope this is helpful.

---

