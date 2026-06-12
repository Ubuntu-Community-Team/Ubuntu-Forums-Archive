---
title: "cpu fan runs at high speed when cpu idle"
date: 2008-08-19
forum: Hardware
---

### Post by vbdanl on 2008-08-19
this is just weird, but maybe someone else has experienced the same problem and knows of a better solution..
i have a emachine T5088 pentium 4 1G ram, 160G hd.  it came with Vista.  I installed Ubuntu, Fedora, and puppy linux.
Vista runs fine.  If I boot into Ubuntu or Fedora after Vista, kacpid process seems to be using half or more of the cpu%, (see by running top command), and the fan inside the box is running at a high speed, and quite noisy.  I expect the fan to ramp up when booting up, and various times when a lot of cpu activity is happening.  It continues to run at high speed, even when the computer is basically idle.  run top command and see 2 kacpid processes near the top, using 50-75% cpu.
Now here is the weirdness.. I read a post where someone had a similar problem, and they suggested pulling the power cord out while the system is running (which i know, is really not what anyone in their right mind wants to do) - i logged off, and at the user login screen pulled the power cord.  when i booted back up, the computer is now quiet, and the kacpid processes appear further down the screen and don't appear to be using any cpu. everything runs quiet, unless i boot back into Vista, then into Ubuntu (or Fedora).  I have checked the bios settings, and can't find anything that I can change having to do with the fan.  I also tried installing the hardware monitor software (can't remember now what it was called), but evidently my hdwe doesn't support the cpu fan speed detection, so it didn't seem to have any value.
i can reboot into linux (after pulling the pwr cord) multiple times without any problem - fan is quiet, case feels cool.  only problem occurs if i go back to vista, then return to linux.  vista runs quiet all the time.
i have other computers running the same versions of ubuntu and fedora and they don't have this problem, but i don't have windows on any of those boxes, and they are older systems..
is there a setting or script that i can install/change to control the kacpid process and/or cpu fan speed?

---

