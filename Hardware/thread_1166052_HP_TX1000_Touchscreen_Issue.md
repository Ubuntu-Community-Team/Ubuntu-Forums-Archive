---
title: "HP TX1000 Touchscreen Issue"
date: 2009-05-21
forum: Hardware
---

### Post by Format C on 2009-05-21
Hi everyone, I have tried ubuntu a few times in the past but with version 9.04 I think I am going to stay.  Anyway, I have an HP TX1000 laptop and I was able to get the touchscreen working, using sudo apt-get install xserver-xorg-input-evtouch.  Calibration worked too.  Now my issue is the screen will register taps, but it will not register drags.  For example, I can try to move this firefox window by pointing the pen at the Title Bar, but when I try to drag the window around, the mouse pointer moves, but the window remains where it was.  In another example, I fired up gimp and tried to draw something.  Once again, it would only register taps.  Any time I tried to actually draw something, the mouse pointer would move, but the paint brush would not follow.  In addition, the computer froze after about a minute of trying to tap in the gimp.

Any ideas on why the computer could be doing this?

Thanks!
Greg


**

---

### Post by mkarnicki on 2009-05-26
Same problem here. Maybe there's a wizkid somewhere out there that will answer the question, so I subscribe to stay posted.

---

### Post by Format C on 2009-05-26
Hey, I saw that they are discussing this issue on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127)

Thanks,
Greg

---

### Post by qhimq on 2009-05-26
THANKS!

```

cd /tmp
sudo apt-get build-dep xserver-xorg-input-evtouch
apt-get source xserver-xorg-input-evtouch
cd xf86-input-evtouch-0.8.7/
rm debian/patches/02-buttonless-device.patch
wget -O debian/patches/02-buttonless-device.patch http://launchpadlibrarian.net/26529094/02-buttonless-device.patch
echo 02-buttonless-device.patch >> debian/patches/series
dpkg-buildpackage
sudo dpkg -i ../xserver-xorg-input-evtouch_0.8.8-0ubuntu3_i386.deb

```

worked for me from Morgan Tørvolt at [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127)

---

### Post by mkarnicki on 2009-06-13
Instead
```
echo 02-buttonless-device.patch >> debian/patches/series

```
shouldn't it be:
```
echo debian/patches/02-buttonless-device.patch >> debian/patches/series
```

Still, failed to build package:
```
Applying patch 21_more_calibration_fixups.patch
patching file evtouch.c
patching file ev_calibrate.c

Applying patch debian/patches/02-buttonless-device.patch
failed! (check stampdir/log/patch for details)
make: *** [stampdir/patch] Error 1
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
```

---

### Post by Milv8 on 2009-06-14
Hi there
i have been having the same problem with the touch screen tx 1000
i add/remove screen calibration.
reboot tx1000
install evtouch again from synaptics
reboot tx 1000 
calibrate touch screen.

"what i think could be a problem is when trying to calibrate the touch screen i was holding the pen/stylus to long on the crosshair,which could act as a double click.

just try short taps on the crosshair.
all working perfectly.

love ubuntu

regards
Milv8:D

---

### Post by Format C on 2009-06-14
Hi, I tried the short taps - still having the same issue.

Thanks,
Greg

---

### Post by REDace0 on 2009-10-28
I've got a tx1000 as well.

I've tried the evtouch2 driver and am having the same problem, i.e. dragging is impossible. I've tried to install the above package, but it fails to build. I'm hoping someone finds a fix to this, because making handwritten documents is currently the only reason I boot Windows on this machine.

---

