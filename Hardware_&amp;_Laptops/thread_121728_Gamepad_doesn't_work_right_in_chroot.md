---
title: "Gamepad doesn't work right in chroot"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by Alabama_Man on 2006-01-25
I made a 32-bit chroot in my 64-bit Ubuntu after this howto:
[http://www.ubuntuforums.org/showthread.php?t=24575&nojs=1#goto_threadsearch](http://www.ubuntuforums.org/showthread.php?t=24575&nojs=1#goto_threadsearch)
I installed in chroot ubuntu-desktop and enabled hardware acceleration. I activated shared memory. In my 64-bit enviroment the gamepad(a ps2 gamepad-clone) it works right in jscalibrator(12 buttons 6 axis driver version 2.1.0.). In my 32-bit chroot it has only 2 buttons and displays driver version 0.8.0.
It works in zsnes with all 12 buttons, even though in the console it says on running it has only 2 buttons. But in Mupen64 the 12 buttons are configurable, but only 2 are usable. In addition every time i starting jscalibrator in chroot or change something in it i get the following error message in the console:
Failed to set joystick /dev/js0 correction values: Invalid argument
can anybody help me getting all 12 buttons to work in chroot?(sorry for my bad english, i'm not a native speaker)

---

