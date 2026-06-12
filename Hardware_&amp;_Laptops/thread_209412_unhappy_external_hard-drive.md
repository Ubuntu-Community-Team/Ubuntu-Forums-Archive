---
title: "unhappy external hard-drive"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by Knightjar on 2006-07-05
Hi, I have a problem with a 200Gb Lacie external hard drive, containing some valuable data I would like to get off. A couple of days ago I was able, briefly, to mount it (it only did read only), but shortly afterwards I couldn't see it at all. There were some nasty rattles coming from inside the case so I've taken it apart and plugged the drive itself into a new case, which seems to have got rid of the physical problems. I can now see it:

```
chrisk@knightjar:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9399    75497436   83  Linux
/dev/hda2            9400        9729     2650725    5  Extended
/dev/hda5            9400        9729     2650693+  82  Linux swap / Solaris

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24792   199141708+  83  Linux

```
I don't know much about how these things are meant to work, but that seems okay.

however, if I try to mount it I get:

```
chrisk@knightjar:~$ sudo mount /dev/sda1 /media/FWdrive
mount: you must specify the filesystem type
chrisk@knightjar:~$ dmesg | tail
[17197620.060000] HFS+-fs: unable to find HFS+ superblock
[17197632.296000] VFS: Can't find an ext2 filesystem on dev sda1.
[17197658.880000] VFS: Can't find ext3 filesystem on dev sda1.
[17197951.264000] FAT: invalid media value (0xe1)
[17197951.264000] VFS: Can't find a valid FAT filesystem on dev sda1.
[17198027.856000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17198027.856000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17198027.856000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17198027.856000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
[17198861.244000] HFS+-fs: unable to find HFS+ superblock

```
I THINK this is meant to be an ext3 disk comprising one single partition. Telling it the type doesn't seem to help:

```
chrisk@knightjar:~$ sudo mount -t ext3 /dev/sda1 /media/FWdrive
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

chrisk@knightjar:~$ dmesg | tail
[17197175.472000] EXT2-fs: group descriptors corrupted!
[17197176.644000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[17197176.836000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[17197176.892000] XFS: bad magic number
[17197176.892000] XFS: SB validate failed
[17197176.896000] XFS: bad magic number
[17197176.896000] XFS: SB validate failed
[17197620.060000] HFS+-fs: unable to find HFS+ superblock
[17197632.296000] VFS: Can't find an ext2 filesystem on dev sda1.
[17197658.880000] VFS: Can't find ext3 filesystem on dev sda1.

```
I've run gpart which gives:

```
chrisk@knightjar:~$ sudo gpart -v /dev/sda1

dev(/dev/sda1) mss(512) chs(24791/255/63)(LBA) #s(398267415) size(194466mb)

* Warning: strange partition table magic 0x2882.
Primary partition(1)
   type: 008(0x08)(AIX filesystem)
   size: 1085474mb #s(2223051520) s(33554434-2256605953)
   chs:  (129/34/10)-(1/0/36)d (2088/170/5)-(140467/57/8)r
   hex:  45 22 0A 81 08 00 24 01 02 00 00 02 00 13 81 84

Primary partition(2)
   type: 001(0x01)(Primary DOS with 12 bit FAT)
   size: 272064mb #s(557187073) s(2184318977-2741506049)
   chs:  (32/8/0)-(771/68/6)d (135967/144/51)-(170650/219/3)r
   hex:  43 08 00 20 01 44 C6 03 01 10 32 82 01 00 36 21

Primary partition(3)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 295204mb #s(604578313) s(33587200-638165512)
   chs:  (2/0/6)-(49/52/10)d (2090/180/11)-(39723/246/20)r
   hex:  85 00 06 02 83 34 0A 31 00 80 00 02 09 22 09 24

Primary partition(4)
   type: 002(0x02)(XENIX / filesystem)
   size: 69892mb #s(143138816) s(285737152-428875967)
   chs:  (832/0/0)-(768/0/0)d (17786/80/23)-(26696/75/3)r
   hex:  89 00 C0 40 02 00 C0 00 C0 00 08 11 00 20 88 08


Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


```
I don't really understand what any of this means, or what it would be best to do now- I presume NOT just run gpart -W (given the exclusive zeros from gpart and the fact it wants there to be 4 partitions not 1)? Incidentally, gparted, with its friendlier GUI says:

/dev/sda1 
194474 Mb
Filesystem: Unknown
Size: 189.92 Gb
Flags:
Path: /dev/sda1
Status: Not mounted
First Sector: 63
Last Sector: 398283479
Total Sectors: 398283416
Warning: Unable to detect file system! Possible reasons are:
-The filesystem is damaged
-The filesystem is unknown to lib parted
-There is no filesystem available (unformatted)

Any help very gratefully received, Thanks!

---

