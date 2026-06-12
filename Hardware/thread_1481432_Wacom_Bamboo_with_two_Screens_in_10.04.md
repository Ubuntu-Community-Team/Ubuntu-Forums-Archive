---
title: "Wacom Bamboo with two Screens in 10.04"
date: 2010-05-12
forum: Hardware
---

### Post by schubber on 2010-05-12
Hello,

i just installed Ubuntu 10.04. Everything worked out of the box beside my Wacom BambooFun Tablet. I use a two screen configuration. With the pen I can use the left half of the left screen only and the right half of the right screen. When i change to relative mode with > xsetwacom "Wacom BambooFun 4x5" "Mode" "Relative" i can use the whole left screen. But if i move to the right screen, i can't move back to the left and the pen "jumps".
I think the problem is how to adjust the tablet to my two screen configuration. I tried with a one screen configuration and the tablet worked flawlessly.
In ubuntu 8.04 i had a custom xorg.conf. But in 10.04 i can't use this any more because the X11-system is changed.
I experimented with xsetwacom and the option twinview but no success. While doing so i found the command > xsetwacon get "Wacom BambooFun 4x5" "Mode" only shows a > 1 I think it should be > Absolute or > Relative Perhaps even a bug in the Driver of the BambooFun? 
I also tried the latest driver from the Linux wacom projekt, but still no improvement.

Any help or suggestions are appreciated ...

---

### Post by gabe_rosser on 2010-08-19
I realise this is a really old thread now, but did you ever get it sorted?

I had the same problem in Ubuntu 10.04 x86_64 with xsetwacom returning "1" for every get command I issued.  When I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=1515562]("http://ubuntuforums.org/showthread.php?t=1515562") it fixed it for me.

---

