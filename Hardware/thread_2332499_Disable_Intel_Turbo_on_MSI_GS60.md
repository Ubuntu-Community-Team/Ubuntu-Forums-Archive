---
title: "Disable Intel Turbo on MSI GS60"
date: 2016-08-01
forum: Hardware
---

### Post by gpaunescu2 on 2016-08-01
Hi,

I hope this is the right place to post this question.
I have a laptop MSI GS60 6QE; CPU is Skylake I7-6700HQ and GPU NVIDIA GTX 970. I had installed Ubuntu 16.04 on it and is working quiet good.
I do some research to disable Intel Turbo, under Ubuntu (I'd like to mention that I disabled from BIOS, but is still enabled in Ubuntu). I found a solution, using msr:
*sudo wrmsr -px 0x1a0 0x4000850089* - where px is the CPU core number (from 0-3).
Is working fine (need module msr to be loaded prior to run the script). 
My need is that I need this to be done automatically after each boot; please help me with this.

Thanks,
Gabriel

---

