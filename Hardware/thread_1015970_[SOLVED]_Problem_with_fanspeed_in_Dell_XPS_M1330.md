---
title: "[SOLVED] Problem with fanspeed in Dell XPS M1330"
date: 2008-12-19
forum: Hardware
---

### Post by KeilanS on 2008-12-19
I just installed Ubuntu via Wubi on my Dell XPS M1330 and it appears to have broken the fan. It used to be completely silent all the time except when gaming. Now I'm sitting here with nothing open but this window (in Vista) and the fan is running.

So why would installing Ubuntu effect the fan inside of Windows? Any suggestions would be much appreciated. I miss my silent laptop! :)

Specs:
Dell XPS M1330
Nvidia GeForce 8400M GS
250GB HDD
T8300 2.4GHz Processor (2 core)
4GB RAM

Thanks,
Keilan

Edit: I forgot to mention this. I am already using the newest bios version (A14)

---

### Post by sdennie on 2008-12-19
Sounds like either a bug with Windows or a bug with the BIOS.  My M1330 is almost identical to yours and I've noticed no increased fan speed under Ubuntu (I don't have Vista).  It wouldn't surprise me if it's a bug with the A14 BIOS though because, it's reporting incorrect temperatures for the CPU.  Maybe that is the cause of the problem.  You may also want to completely shutdown the machine (not reboot) and see if it fixes Windows.  I think that soft-boots don't completely reset everything under BIOS control.

---

### Post by KeilanS on 2008-12-19
It worked fine under the A14 Bios with the newest graphics drivers with just Vista, so it's definately installing Ubuntu that did it. I will give it some time (and some hard restarts) and see what happens, and I haven't updated the Ubuntu drivers yet either, so maybe that will help.

---

### Post by blomkaal on 2008-12-23
I've got the same problem with my M1330 after installing 8.10... I'm not sure whether the issue was there in 8.04 as well, though.

I'm also running a dualboot with Vista, not sure which bios-version I have, though.

I've searched around for the past few days, looking for a solution on how to adjust the fanspeed, but I can't seem to find anything that works...

Any help would be much appreciated, as the noise is driving me crazy

---

### Post by nick09 on 2008-12-23
On boot-up the BIOS version should be on the left bottom corner of your screen.

---

### Post by KeilanS on 2008-12-28
Okay, I switched Nvidia driver Version 177 with Version 173 and the problem went away.

SOLVED.

---

