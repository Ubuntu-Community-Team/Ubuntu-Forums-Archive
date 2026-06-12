---
title: "Ubuntu 8.10 and 9.04 beta LiveCD will not boot"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by GourdCaptain on 2009-03-28
A friend of mine has an eMachines T2484 desktop (Intel Celeron 2.4 gHZ, Geforce FX 5200, 512 MB RAM) that began crashing at the boot screen when it was updated from 8.04 to 8.10.

It crashes at the booting screen with the progress bar, approximately at the time it stops for several seconds to recognize USB devices (I think.)

The crashing kernel is 2.6.27-11

An older kernel in the GRUB list (2.6.24-23) booted to X, but was unstable and internet/ethernet would not work. I just tried a 9.04 beta LiveCD, and it crashes as well at the same place as 8.10 once "Try Ubuntu...." is selected.

---

### Post by Partyboi2 on 2009-03-28
Try booting without the splash screen. At the main menu of the live cd press F6 and change 'splash' to 'nosplash'

---

