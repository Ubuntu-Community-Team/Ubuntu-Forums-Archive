---
title: "System freezes within 30-60 seconds of being logged in"
date: 2010-11-20
forum: Hardware
---

### Post by El Cris on 2010-11-20
My system freezes whenever I'm booting normally. When booting in recovery mode and starting failsafeX (with low-graphics-mode) I can normally use it (albeit lacking graphics-acceleration). So I've configured X to use the vesa-driver, as I thought the ati-drivers gave me problems but it still freezes when booted normally. Any Ideas what to check next? I've been hunting this the whole day now and am running out of ideas.

Motherboard: albatron k8x800 pro
CPU: amd athlon 64 3000+
Graphics: ati radeon hd 3850

What else I've tried so far (AFAIR):
- removing rt2500-based wifi pci-card
- installing latest ati-drivers, so not only installing fglrx from the repository
- trying to force AGP 4x with ```
Option "AGPv3Mask" "0x00000002"
``` as the AGP speed in bios is shown as "8x" and grayed out, so not changeable
- setting the voltage for agp from 1.5 to 1.6
- changing AGP Aperture size to 128, 256, 512
- various kernel boot options to no avail: ```
acpi=off nosmp maxcpus=0 noapic nolapic
```

---

### Post by El Cris on 2010-11-20
I should probably add that I had to install using the alternate-cd (text mode), as the live-cd would freeze too.

Both the x86 and the x86_64 install-cds would freeze.
For the time being I've installed using the x86 alternate cd.

Edit: Windows XP was installed on this machine before and there were no problems playing 3d games etc.
I just want to get this thing running under linux with a little bit of acceleration. I think I'd even be satisfied for the moment if it would run with 2d acceleration and 100hz @ 1600x1200. But I'm really wondering what causes the problem even with the vesa-driver...

Any suggestions on what else to try are highly appreciated!

---

### Post by El Cris on 2010-11-21
bump

I hope it's ok to bump already, it's been 10 hours and my thread is on page 2 where only a few will go I guess. If you do have a problem with that, please let me know.

---

### Post by El Cris on 2010-11-21
Using google I've found two threads on these forums that show the same problem with the same motherboard (k8x800 pro OR k8x800 pro 2).

_[In this thread]("http://ubuntuforums.org/showthread.php?t=398913")_, **CRO-MAGnum PI** gives a solution to my problem. I've had already disabled APIC in bios but now that I've removed 1 ram stick and left 1 in dimm1, my system is now working with 3d acceleration. I'd like to use 2gb instead of 1 obviously, but this is better than nothing for now. I'll try combinations of using other dimm-slots later.

In _[this]("http://ohioloco.ubuntuforums.org/showthread.php?t=41300")_ and _[this thread]("http://wwww.ubuntuforums.org/showthread.php?t=40909")_, **Krogen** complains about the exact same issue. I know these threads are 5 years old and Krogen was last active one year ago, but could someone please send him a private message about it? I wasn't allowed to, because you're required to have written at least 75 posts.

Thanks :-)

---

