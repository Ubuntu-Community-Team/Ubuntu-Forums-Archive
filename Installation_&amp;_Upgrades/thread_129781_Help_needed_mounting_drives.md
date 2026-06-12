---
title: "Help needed mounting drives"
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by gingermark on 2006-02-14
Hi,

Have recently upgraded my computer. I installed Kubuntu on a new harddrive, but I've forgotten how to mount my other drives.

I've transferred my old harddrives to my new setup, and need to mount them, mainly to copy all the stuff I need off them. I then plan to reformat them to ext3 and use them for media storage.

I typed sudo fdisk -l, and got the following:

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1084     8707198+   c  W95 FAT32 (LBA)
/dev/hda2            1085        9683    69071467+  83  Linux
/dev/hda3            9684        9729      369495    5  Extended
/dev/hda5            9684        9729      369463+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19457   156288321    b  W95 FAT32

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         653     5245191    b  W95 FAT32
/dev/sda2            5599       30401   199230097+  83  Linux
/dev/sda3   *         654        5393    38074050   83  Linux
/dev/sda4            5394        5598     1646662+   5  Extended
/dev/sda5            5394        5598     1646631   82  Linux swap / Solaris

Partition table entries are not in disk order

To explain,

sda is my new SATA drive, and I placed a 5GB FAT32 partition (sda1) at the start just in case I need to bung Windows on at somepoint. sda2 is a 200GB partiton that will store my data while I reformat the other drives. sda3 - sda5 were created by Kubuntu when I installed this time round.

hda1 is my old Windows install, hda2 being my old Kubuntu install.

Ideally I'll need to mount sda2, hda1+2, and hdb.

After I've moved the files I want across to sda2, I'll wipe hda and hdb and format them to ext3.

Which leads to my final question - how does one decide on character coding? (that's probably not even the correct term - but I mean utf8, iso9661 (or whatever)).

I'm looking for things to not be case specific, and to support foreign characters, especially letters with umlauts and accents. This is mainly because of my music collection, and in the past such characters haven't been dispayed correctly, even if the data was contained within id3 / ogg tags.

Many thanks for any advice / help you can give,

best regards,
gingermark.

---

### Post by gingermark on 2006-02-14
I ended up mounting my drives using kcontrol's GUI.

---

