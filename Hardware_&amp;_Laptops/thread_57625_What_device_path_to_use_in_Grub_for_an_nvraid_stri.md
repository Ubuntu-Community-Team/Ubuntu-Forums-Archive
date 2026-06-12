---
title: "What device path to use in Grub for an nvraid stripe"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by hartz on 2005-08-17
I am having what seems to be a common problem - that of dual-booting Windows and Ubuntu, using Grub as boot-loader, having Windows on a raid-0 nvraid drive.

I am hoping to dedicate a 120 GB SATA drive to Linux.  (4 other drives in various Raid-sets are being used by Windows presently)

I initially got Ubuntu to install on the 120GB drive set as a JBOD device using NVRAID on the Gigabyte GA-K8NXP-SLI motherboard.  Ubuntu installed but after the reboot Grub gave me "Error 21".  I figure grub device paths during instalation and during boot are not identical.

I then removed the drive from the NVRAID control through BIOS options, and used it as a normal drive.  The install again went through fine, but this time Grub gave me error 17.

I think I will be able to solve this, possibly with correct BIOS settings and manually editing the grub conf files.  Maybe someone here can give me some guidance.

Once I get this working I will want to make one of the raid-0 sets a boot-option in Grub.  The ubuntu installer does not recognize windows on the raid-0 stripe (it does not like the partitioning on this stripe set at all) ... So my question is what device would I assign for the boot option to load windows.

Note: I also have some raid sets on the SI3114 controller.

Thanx!
  _Hartz

---

