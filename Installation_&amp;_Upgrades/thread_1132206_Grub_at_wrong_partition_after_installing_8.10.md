---
title: "Grub at wrong partition after installing 8.10"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by Yanisae on 2009-04-21
Hi people,

  My problem is probably quite simple to solve, but I have looked for an answer to suit _my_ problem and can't find a good one.

  I had previously installed 7.10 at one partition at my first (and by that time only) PATA drive. It was a dual OS drive with a bunch of partitions. All fine.

  After that I installed 2 SATA drives with HW RAID. All fine for both OSs.

  Today, I've decided to reinstall both OSs. I went through all Ubuntu 8.10 64bit installation process. After reboot, I cannot reach Grub.

  The point is that when Ubuntu finds a RAID config, it sees all drives (incl. non-RAID ATA ones) as scsi0, scsi1, or similar. Therefore, when it installs (by default) Grub at (hd0) it's in fact installing at sda1 (first RAID drive) and not sdc1 (master ATA drive). I don't understand why changing the old name system, and why Ubuntu doesn't find the bootable volume and just installs Grub there (or sets it "default").

  I've tried using the live CD, things like grub-install /dev/sdc1 and grub-install /dev/hda0 but no way. It says something like "not a block device". I can always make a reinstall from scratch but there's surely a better (and faster option).

  I want my box to boot from ATA drive, there's no option to boot from USB. Would someone help me here ?

  Thanks in advance !

---

### Post by meierfra. on 2009-04-21
Boot from the Ubuntu Live CD, open a terminal,

```
sudo grub 
```

and at the "grub>" prompt.



```
 find /boot/grub/stage2 
```

This will return (hdX,Y), where X and Y are some numbers, like (hd2,0)
(if it returned 'file not found', try  'find /grub/stage2' and  'find /stage2')


Still at the "grub>" prompt:


```
root (hdX,Y)
setup (hdX)
quit

```

(here X and Y need to be replaced by the numbers you got from "find /boot/grub/stage2")

---

### Post by ronparent on 2009-04-22
The standart 8.10 desktop install disk does not see your raid array. I can't tell from your post what is installed where, but all that has to be sorted out to complete your install. The following site tells how to install to a fake raid setup:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Normally you need to install from the alternate cd (to see the raid partions during partitioning). There is an alternate method outlined in the reference above. If the installs have already been done to the raid array you may be able to pickup where you left off by installing dmraid and running it to map your array to /dev/mapper if you are using raid1 (mirroring). If you have already configured your intel raid bios for raid0 (stripped) you may have to start all over again because you may have installed to one disk not the array which spans both disks. Once everything is sorted out with dmraid, you can use the steps outlined in the above post to setup your grub.

---

