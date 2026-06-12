---
title: "STAC92XX and Audacity Problem"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by wylie348 on 2007-06-04
For some reason I cannot use Audacity properly in Feisty?!  I want to record the audio stream currently playing in the speakers (streaming radio), but Audacity will not let me record.  I have tried every setting offered under preferences for audio and record, but no joy?
Thanks in advance for any help!

Hardware:  Fujitsu T4210 Tablet, Stac92xx

---

### Post by Ferret-Simpson on 2007-07-26
The same goes for SKYPE. The issue is not in the hardware, or in Audacity, it's just that the ALSA driver for the T4210 is Borked. Send a bug report to the ALSA team.

I R HAS SAME PROBLEM.

I R HAS EXTERNAL SOUND CARD INSTEAD. :)

It is after all, a better situation than Ahem. >.> <.< "Darwin" on the T4210. Darwin has no PCI support for the T4210 so half the devices don't work. (It reaches an empty bus and stops enumerating.) On top of that, the Audio in doesn't work, and the audio out works through socket and speakers simultaneously only.

---

