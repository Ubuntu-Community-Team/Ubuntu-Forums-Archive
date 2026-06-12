---
title: "Gamepad and Znes"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by Lucidio on 2006-08-07
Good afternoon to all!

i have a genius maxfire minipad gamepad but znes dont recognize the directions (the rest of the buttons seems to work fine).

i donwloaded and installed the packages joystick and jscalibrator and i calibrate my pad, which means that ubuntu recognize it.

When i enter in the configuration screen for znes to configure my pad, the program dont let me asign the direction of my pad.

any ideas?

---

### Post by dfa_geko on 2006-09-04
Hi Lucidio,

I had the same issue as you. I had to do a "sudo chmod 666 /dev/input/js0" inorder for my DPad and analog joystick to work. Read this thread: [http://ubuntuforums.org/showthread.php?t=28538](http://ubuntuforums.org/showthread.php?t=28538) 

I followed it and got mine to work! Good luck!

---

