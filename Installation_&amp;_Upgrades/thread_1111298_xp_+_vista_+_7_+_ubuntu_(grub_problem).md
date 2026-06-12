---
title: "xp + vista + 7 + ubuntu (grub problem)"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by rewolf on 2009-03-30
Okay, here's the story. When i got this computer a few weeks ago, i partitioned my 500gb into 5 partitions. I installed xp,vista,7,kubuntu810,(swap space) on the partitions (in that order).  All worked fine, (grub picked up the vista loader etc).  But i later had to reformat, so i recreated the exact same partitions but only installed xp and vista for the time being.
After a week i decided to install 7 and ubuntu onto the remaining partitions.  But this time the ubuntu installation crashed with a grub-install error code 1 (target was hd0).

Does anyone know why it does this, and what i can do to fix this?  from the live CD, fdisk -l gives:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11dd11dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27414   220202923+   7  HPFS/NTFS
/dev/sda2           27415       60800   268173045    f  W95 Ext'd (LBA)
/dev/sda5           27415       49606   178257208+   7  HPFS/NTFS
/dev/sda6           49607       53522    31455238+   7  HPFS/NTFS
/dev/sda7           53523       60661    57343986    e  W95 FAT16 (LBA)
/dev/sda8           60662       60800     1116486   82  Linux swap / Solaris

```
If (after the failed installation) i mount the installed partition, the grub dir has:
```

ubuntu@ubuntu:~$ sudo mkdir /mnt/tmp
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda7 /mnt/tmp/
ubuntu@ubuntu:~$ ls /mnt/tmp/boot/grub/
default     e2fs_stage1_5  jfs_stage1_5    reiserfs_stage1_5  stage2
device.map  fat_stage1_5   minix_stage1_5  stage1             xfs_stage1_5

```
If i try run grub-install on the partition i get:
```

ubuntu@ubuntu:~$ sudo grub-install /dev/sda7
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

I'm quite a noob to playing with grub etc. so all this stuff might be completely irrelevant, but i would REALLY appreciate some help.
I don't mind if i i use grub as the main bootloader or the vista one, as long as both OS' are accessible

Thanks * 9001 in advance

rewolf

---

### Post by lemming465 on 2009-03-31
It's a little odd to install an ext3 filesystem on a partition of type 'e'; I'd change it to '83'. (fdisk /dev/sda, "t" command)  Less confusing that way.

Try **sudo grub-install --root-directory=/mnt/tmp /dev/sda7** and see if that does better.

---

### Post by Mark Phelps on 2009-04-01
Did Ubuntu ever work with GRUB installed on the FAT-16 partition? Only asking because I saw another thread where someone was attempting to install GRUB in a FAT (16) partition and it kept failing due to filenames being too long.

---

