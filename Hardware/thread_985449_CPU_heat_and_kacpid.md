---
title: "CPU heat and kacpid"
date: 2008-11-17
forum: Hardware
---

### Post by Sorex on 2008-11-17
I've always had a problem with CPU usage, the source being the recognised problem of kacpid constantly running. But one day out of the blue, while using Hardy, the problem disappeared, CPU usage dropped from 80% to virtually nothing, and CPU temp dropped from 70C to 35C.

Then, with an update, the problem returned.  So I updated to Intrepid, but this hasn't helped.  Weirdly the temp isn't as high, only 60C, and CPU is only at 50%, but this is still clearly a strain on the computer and the battery.

kacpid can't be killed, and if you try to stop it by turning off acpi in the GRUB then the computer dies and requires an OS reinstall.

There is one way of sorting it out - hibernate and wake up again.  This for some reason takes ages, and sometimes causes the laptop to crash on wake-up, but if it does wake-up then kacpid is gone, CPU usage is nothing and the temperatures are fine.

Anyway, although I've spent hours trawling forums for a solution my only option now is to make this post: HELP!

It's a JFT00 laptop, with a T5450 (2x1.66GHz), 2G RAM.

---

