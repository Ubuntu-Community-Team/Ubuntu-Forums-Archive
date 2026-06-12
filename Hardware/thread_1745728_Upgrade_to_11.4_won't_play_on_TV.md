---
title: "Upgrade to 11.4 won't play on TV"
date: 2011-05-01
forum: Hardware
---

### Post by hifidan on 2011-05-01
I just upgraded my Sony Vaio laptop and I cannot diaplay videos on my 52 inch Sony.I was able with the previous version. I run Intel Pentium M 1.7 Ghz 2 Gig RAM, and the display card is a Intel (R) 915GM,GMS,910GMI,Express Chipset. The video displayed is all jagged and doesn't refresh properly on the TV but works fine on laptop
Help please.:confused:

---

### Post by SeijiSensei on 2011-05-01
If you see the grub menu at startup, try using your older Linux kernel.  The upgrade should have preserved the kernel you were using before.

If you don't see the menu, hold down the shift key during boot.

If this fixes the problem, there's likely an issue with the Intel video driver in the newer kernel.  Let us know what happens.

---

