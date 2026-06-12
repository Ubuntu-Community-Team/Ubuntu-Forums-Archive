---
title: "Dual boot installation with Windows 7 Already installed."
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by deey001 on 2009-03-30
Ok here is my setup.

Asus P5E Mobo
hardware raid 10 (with Windows 7 installed)
SATA 300GB (Data)
SATA 500GB (Ubuntu)

I already had windows 7 installed and wanted to dual boot with ubuntu 8.10. I installed Ubuntu on the 500GB Drive and when setup was complete the machine just booted me back into windows (no GRub).

Is there a way without destroying the RAID to get Grub installed so i can boot both systems?

When i am booted into the Ubuntu Live CD and run an Fdisk i can see all the drives individually grub doesn't list it as a RAID.

Any information would help greatly.

---

### Post by Mark Phelps on 2009-03-31
Don't know squat about RAID, but my guess is that Ubuntu tried to install GRUB to the RAID array and failed for some reason.

You have a couple of options.

1) Install EasyBCD to your Windows 7 and configure it to add an entry for Ubuntu to the Windows 7 boot menu.  You can get EasyBCD from NeoSmart and check their forums for How-to's for doing this.

2) You can try reinstalling and messing aroung with GRUB, installing it to your Ubuntu partition and adding a stanza manually for Windows 7.

---

