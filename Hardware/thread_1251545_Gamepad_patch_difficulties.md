---
title: "Gamepad patch difficulties"
date: 2009-08-27
forum: Hardware
---

### Post by dylanb on 2009-08-27
Hello all,
I'm having some difficulty getting a gamepad (logitech dual action) setup correctly. I have used jscalibration and jscal to get the gamepad calibrated but some of the axes are not correct. The dpad and the left stick are switched, i.e. dpad has range 1 to 258 and stick has range -1 to 1.. It seems that ubuntu 8.04LTS doesn't have the -u option used to switch axes. This is available for 9.04. I found a patch in the form of a .diff file, and also a recompiled version for 7.10 64bit. ([http://ubuntuforums.org/showthread.php?t=761044](http://ubuntuforums.org/showthread.php?t=761044)) I tried to unzip that and "make clean      make" the file, but it didn't work. How can I use the patch? I don't know where jscal.c is located in my file system. I'm a linux noob if you hadn't noticed :)
Thanks,
Dylan.

---

### Post by CrazyMezei on 2009-08-28
get rid of jscalibrator... thats what i did and now I'm playing games without a hitch...

---

### Post by dylanb on 2009-08-29
Thanks. I tried that but no success. I really think the issue is just related to axes being switched. Unfortunately jscal -u is not available for ubuntu 8.04LTS. I can't upgrade because I have a project that relies on 8.04. If someone could please tell me where to find jscal.c and how to apply a .diff file then I might be in business.

---

### Post by RobbMeex on 2010-01-03
try deleting /home/username/.joystick
Reset
That did it for me.

---

