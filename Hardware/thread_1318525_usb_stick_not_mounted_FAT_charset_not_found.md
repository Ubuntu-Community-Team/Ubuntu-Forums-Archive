---
title: "usb stick not mounted: FAT charset not found?"
date: 2009-11-07
forum: Hardware
---

### Post by kawazu on 2009-11-07
Folks;

after upgrading 9.04 -> 9.10, my USB sticks that worked flawlessly in 9.04 ceased working. While in 9.04 I could easily mount them using the icon appearing on the desktop as soon as the stick was plugged in, in 9.10 there is just an error message popping up that the device can't be mounted, and in dmesg I see this error:

[  152.618697] FAT: IO charset ISO-8859-15 not found
[  152.652679] FAT: IO charset ISO-8859-15 not found


Mounting the device (/dev/sdc1, in this case) manually after such an attempt fails with mount complaining that this device does not exist, even though it was reported to be found in dmesg before?! What could be wrong here?

TIA and all the best,
Kristian

---

### Post by mariano_rcia on 2009-11-08
A similar thing happened to me. My usb sticks worked just fine with 9.04 but after upgrading to 9.10 i can't access them. I had to reboot to get their filesystems mounted.

---

### Post by kawazu on 2009-11-09
> **mariano_rcia said:**
> A similar thing happened to me. My usb sticks worked just fine with 9.04 but after upgrading to 9.10 i can't access them. I had to reboot to get their filesystems mounted.

Hmmm, already tried a couple of combinations here (rebooting with stick attached, attaching stick after rebooting/logging in, ...), same effect in each case. Adding to this, however: This seems just the problem on one of my machines, my work notebook (which also has seen an upgrade 9.04 -> 9.10) doesn't expose this behaviour... :(

---

### Post by mariano_rcia on 2009-11-16
I've got my usb sticks working again after applying all the security and recommended updates with the Update Manager. Back to normal. Thanks though

---

