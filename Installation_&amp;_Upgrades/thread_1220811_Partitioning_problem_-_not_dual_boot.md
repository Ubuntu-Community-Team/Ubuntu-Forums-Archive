---
title: "Partitioning problem - not dual boot"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by hnmcc on 2009-07-23
I have a Lenovo Thinkpad X25 with Mandriva Linux; it also has an IBM toolset that came pre-installed on the laptop with WinXP Pro. There is no working WinXP installation.

I now wish to replace Mandriva with Ubuntu as a single-boot system.  I also want to be SURE that the IBM tools remain available.

I am very confused by the partitioning options during Installation (especially as they don't correspond to what the documentation says I should be seeing - I'm offered no "guided" path, for example).

The **Prepare Disk Space** screen says "this computer has several operating systems on it".  It analyses the disk as follows:

/dev/sda1  66.4MB
/dev/sda4  27.9GB
/dev/sda5   5.1GB - Mandriva Linux
/dev/sda2   4.1GB - Windows XP

Neither of the first two items (install side-by-side, or use whole disk) is right for me, so I have to go with "Specify partitions manually", which takes me to **Prepare Partitions**.  It analyses the disk as follows:

sda1 (ntfs)      66.4MB
sda4 (ext3)      27.9GB
sda5 (linux-swap) 5.1GB
sda2 (fat32)      4.1GB

I attach a couple of (wobbly but readable) snapshots of these two screens.

To achieve what I describe in para 2, what (in detail) should I do here??  I have tried "following my nose", but without success.  I need help!

:confused:

---

### Post by ajgreeny on 2009-07-23
This shows that the IBM tools are on either sda1, which is the ntfs windows partition, I imagine, or, more likely, sda2, if they were on a separate partition.

It would be useful to get more info on the partitions from your ubuntu live CD, opening a terminal and running ```
sudo fdisk -l
``` Copy the output here and it may help more with the details of what to advise.

I suspect, however that it will be much easier to use manual partitioning when you get to that section of the install, but let's have those details from fdisk first.

---

### Post by hnmcc on 2009-07-24
Thanks! :)

Here's the fdisk output:
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           9       68008+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4323        4864     4347000   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            3657        4323     5352449    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4              10        3656    29294527+  83  Linux
/dev/sda5            3657        4323     5352448+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1999 MB, 1999634432 bytes
16 heads, 32 sectors/track, 7628 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16        7628     1948736    e  W95 FAT16 (LBA)
```

---

### Post by presence1960 on 2009-07-24
At the prepare disk space window choose the manual option. On the next window highlight your sda4 partition and click edit. Set the paramaters for that partition: use as-> choose ext 3 or ext4 filesystem. Check the format box so it formats that partition and mountpoint select /. At the Ready to install window click the advanced button and choose sda to put GRUB on MBR (see attached screenshot). Proceed with the install. Swap should be auto set since the partition already exists.

---

### Post by hnmcc on 2009-07-26
Thanks everyone: all's well. :D

---

