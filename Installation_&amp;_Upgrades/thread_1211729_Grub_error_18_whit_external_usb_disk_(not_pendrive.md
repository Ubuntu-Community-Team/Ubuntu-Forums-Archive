---
title: "Grub error 18 whit external usb disk (not pendrive)"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by danin on 2009-07-13
Hi, 

I installed Ubuntu 8.04 on internal disk, but when I moved it to an external usb box I get an "Grub Error 18.."
I don't have  to much experiencie working with Grub.
So, these ones was the steps made it in my laptop:
1. I remove my original disk (120Gb) to put the new one (320Gb).
2. The new one already has information on a partition.(200Gb)
3. I installed the Ubuntu and created two patition more.
4. Reboot the new installation and everithing ok, then I remove the new disk(320Gb) to put it into the external usb box.
5. I try to boot from the usb and I get the error.

Here you have the fdisk output:(sorry is in Spanish but the information is the same).
The first one is my original disk.

ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 120.0 GB, 120034123776 bytes
240 cabezas, 63 sectores/pista, 15505 cilindros
Unidades = cilindros de 15120 * 512 = 7741440 bytes
Identificador de disco: 0x31a431a3

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5449    41194408+   7  HPFS/NTFS
/dev/sda2            5450       15505    76023360    f  W95 Ext'd (LBA)
/dev/sda5            5450       15505    76023328+   7  HPFS/NTFS

Disco /dev/sdb: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x01af75a3

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1       25497   204800368+   7  HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/sdb2           25498       26226     5855692+   5  Extendida
/dev/sdb5           25498       26104     4875696   83  Linux
/dev/sdb6           26105       26226      979933+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

So, I'd like to only work with Ubuntu from the external box, and now I don't know how to restore it to boot. I'm afraid to do something that modifies the main disk while I restore or modify the Grub.

Could you guide me to solve this problem?

Thanks!
Danin.

---

### Post by quixote on 2009-07-15
If I understand it right, you were using an internal hard drive from which Ubuntu could boot.  Then you moved that hard drive to a USB enclosure, but you'd still like to be able to boot Ubuntu from it.  Is that right?

One important point: the computer, and hence grub, number drives sort of based on when they find them during boot up.  So the first partition on the first internal hard drive is (hd0,0).  If you move that to a USB enclosure and it becomes the second hard drive, grub will see it as (hd1,0).  Not the same thing at all, even though it's the same physical object.  In your case, since Ubuntu is not on the first partition, it might be (hd1,4).  This [link]("http://linuxmint.com/wiki/index.php/How_to_repair_your_grub") has a lot of useful info on how to find boot partitions for grub and and set them up.

The error 18 is saying that the BIOS is having a hard time finding the partition, which can happen if it's too far away. eg [caljohnsmith in another thread]("http://ubuntuforums.org/showpost.php?p=6153380&postcount=5"): > in order to prevent a Grub error 18, the bottom line is that you need to move your Ubuntu boot files closer to the front of the drive so that the BIOS can access them on start up. The usual way of doing this is to create a ~200 MB /boot partition at the beginning of the drive, and you should be all set. You can do that during the Ubuntu installation by creating that 200 MB partition and specifying its mount point as "/boot".

It sounds like some of the drives are huge, so that may well be part of the problem.

One last caveat:  USB drives that are slow to spin up may not be "awake" before the BIOS gives up.  See for instance [here]("http://ubuntuforums.org/showpost.php?p=6449046&postcount=4").  Apparently the solution is just to keep trying to boot until it goes.  

Hope that helps to some extent!

---

