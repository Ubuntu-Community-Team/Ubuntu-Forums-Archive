---
title: "howto make boot CD to boot into installed system on pcmcia harddisk"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by robert_kofler on 2005-08-05
ubuntu 5.04

my notebook (compaq presario 701EA) **has no harddisk**, but a working cd/dvd drive.
I also installed a toshiba pcmcia hdd (4,5GB).

ubuntu 5.04 was able to install the system on the pcmcia drive :-)
but because of missing pcmcia-boot option in my bios it does not boot.
... a bios update can only be done under windos :-(

Booting with isolinux and additional params like root=/dev/hda3 causes a kernel panic because of missing pcmcia support at that stage of the boot process (either inside initrd or in the kernel).

Question(s): 
howto can i make a boot CD to **boot the *installed*** system on the pcmcia harddisk.

I tried mkinitrd and mkisofs which worked quite well... 
I also copied the pcmcia_core.ko,pcmcia.ko to /lib/modules/-version-/initrd as suggested in the man-pages, so that the mkinitrd skript could find them ... but again the new bootdisk caused a kernel panic.

does anybody know how to modify the shipped ubuntu 5.04 initrd to continue on my pcmcia harddisk instead of installing a new system?

Robert--

---

