---
title: "Help extracting a partition with parted?"
date: 2005-11-13
forum: General Help
---

### Post by grendel_khan on 2005-11-13
I recently had a machine crash horribly on me. Spinning metal, and all that. I was able to recover one of the drives, which still spins up, detects and all that. The drive had a single ext2 partition on it, set as primary (it was a boot drive), as well as an extended partition containing some swap space.

The drive was detected as /dev/hdc on bootup. (/var/log/syslog says hdc: Maxtor 82100A4, ATA DISK drive). To my surprise, ls /dev/hdc* gave only:

```
me@hekyll:~/RESTORE$ ls /dev/hdc* -l
brw-rw----  1 root disk 22, 0 2005-11-12 22:14 /dev/hdc
brw-rw----  1 root disk 22, 1 2005-11-12 22:14 /dev/hdc1
```

Curious; to my understanding, there should have been a /dev/hdc5 for the logical (swap) partition, as well as a /dev/hdc2 for the extended partition. But no matter. I attempted to mount /dev/hdc1, but was told that the filesystem contained errors, and started panicking.

To rule out hardware difficulties, and because I was nervous that his drive, too, would explode into magnetic shrapnel at any moment, I snagged the data from it thusly:

```
$ sudo dd if=/dev/hdc | pv | sudo dd of=hdc
$ sudo dd if=/dev/hdc1 | pv | sudo dd of=hdc1
```

(The 'pv' bit was so I could make sure it didn't get stuck; it's just a pipe viewer. Nifty tool.) I got two files; /dev/hdc was 32256 bytes larger than /dev/hdc1. 'file' detected them as follows:

```
me@hekyll:~/RESTORE$ file hdc*
hdc:  x86 boot sector
hdc1: x86 boot sector, extended partition table
```

Is it supposed to be like that? Bootloader on the drive, as well as on the partition? Hmm. I fired up fdisk, and got the following:

```
me@hekyll:~/RESTORE$ fdisk hdc
You will not be able to write the partition table.
You must set cylinders.
You can do this from the extra functions menu.

Command (m for help): p

Disk hdc: 0 MB, 0 bytes
64 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

Device Boot      Start         End      Blocks   Id  System
  hdc1   *           1        1023     2062336+  55  EZ-Drive
Partition 1 has different physical/logical endings:
     phys=(1021, 63, 63) logical=(1022, 63, 63)
```

EZ-Drive? What the crap? This was the boot drive for an old, nay ancient, Linux Mandrake 7.2 system; I don't think I'd ever heard of EZ-Drive, and I'm pretty sure that old Mandrake system hadn't either. So why was the use of this "EZ-Drive" transparent before and not now? I went, nervously, to sfdisk (taking a cue from the fdisk man page) to see what it would see.

```
me@hekyll:~/RESTORE$ sfdisk -l hdc
Disk hdc: cannot get geometry

Disk hdc: 0 cylinders, 0 heads, 0 sectors/track
detected Disk Manager - unable to handle that
 hdc: unrecognized partition table type
No partitions found
```

Disk Manager? Never heard of it. Perhaps EZ-Drive is **a** Disk Manager? Hmm. The [Large Disk HOWTO](http://www.linux.com/howtos/Large-Disk-HOWTO-8.shtml) makes reference to "EZ-Drive" and "OnTrack DiskManager". Hmm; the translation process involved skipping the first 63 sectors (=31.5kB=32256 bytes) so that agreed with what I'd seen. Perhaps treating the image of hdc1 as an entire disk would work?

fdisk:

```
me@hekyll:~/RESTORE$ fdisk hdc1
You will not be able to write the partition table.
You must set cylinders.
You can do this from the extra functions menu.

Command (m for help): p

Disk hdc1: 0 MB, 0 bytes
64 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

Device Boot      Start         End      Blocks   Id  System
hdc1p1               1         914     1842561   83  Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 2, 1) logical=(0, 1, 1)
Partition 1 has different physical/logical endings:
     phys=(913, 63, 63) logical=(913, 62, 63)
hdc1p2             914        1023      219744    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(914, 0, 1) logical=(913, 63, 1)
Partition 2 has different physical/logical endings:
     phys=(1022, 63, 63) logical=(1022, 62, 63)
hdc1p5             915        1023      219712+  82  Linux swap / Solaris
```

Hmm. The warning about the adjustment of one sector seems to agree with the bit about Disk Manager in the Large Disk HOWTO. I still don't understand how it got on there; the disk has not been used between the old machine's crashing and today.

sfdisk:

```
me@hekyll:~/RESTORE$ sfdisk -l hdc1
Disk hdc1: cannot get geometry

Disk hdc1: 0 cylinders, 0 heads, 0 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/64/63 (instead of 0/0/0).
For this listing I'll assume that geometry.
Units = cylinders of 2064384 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
   hdc1p1          0+    913-    914-   1842561   83  Linux
                start: (c,h,s) expected (0,1,1) found (0,2,1)
                end: (c,h,s) expected (913,62,63) found (913,63,63)
   hdc1p2        913+   1022-    109     219744    5  Extended
                start: (c,h,s) expected (913,63,1) found (914,0,1)
                end: (c,h,s) expected (1022,62,63) found (1022,63,63)
   hdc1p3          0       -       0          0    0  Empty
   hdc1p4          0       -       0          0    0  Empty
   hdc1p5        914    1022-    109-    219712+  82  Linux swap / Solaris
                start: (c,h,s) expected (914,0,1) found (914,1,1)
                end: (c,h,s) expected (1022,62,63) found (1022,63,63)
```

Now I'll just have to extract that partition. But how? parted is a recovery tool, but its cp command only allows for one partition on one device to be copied to another partition on another device. I want to extract the partition so that I can mount it as a loopback device and weed through the files on there. (Simply copying the files off into my current filesystem is a possibility, but I'd prefer to keep it as a drive image.) parted would seem to be the right tool for this, but I can't find anything in the documentation about this particular task.

One more bit of information, from my dmesg, on the kernel detecting the drive as an "EZ-Drive":

```
[4294670.552000] Probing IDE interface ide0...
[4294670.936000] hda: WDC WD1600JB-00GVA0, ATA DISK drive
[4294671.344000] hdb: _NEC CD-RW NR-9100A, ATAPI CD/DVD-ROM drive
[4294671.423000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.423000] Probing IDE interface ide1...
[4294671.807000] hdc: Maxtor 82100A4, ATA DISK drive
[4294672.113000] hdd: probing with STATUS(0x00) instead of ALTSTATUS(0x50)
[4294672.266000] hdd: probing with STATUS(0x00) instead of ALTSTATUS(0x50)
[4294672.419000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.419000] Probing IDE interface ide2...
[4294672.932000] Probing IDE interface ide3...
[4294673.445000] Probing IDE interface ide4...
[4294673.957000] Probing IDE interface ide5...
[4294674.476000] hda: max request size: 1024KiB
[4294674.493000] hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(66)
[4294674.495000] hda: cache flushes supported
[4294674.495000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 > p3
[4294674.543000] hdc: max request size: 128KiB
[4294674.544000] hdc: 4124736 sectors (2111 MB) w/256KiB Cache, CHS=4092/16/63, (U)DMA
[4294674.544000] hdc: cache flushes not supported
[4294674.544000]  /dev/ide/host0/bus1/target0/lun0: **p1[EZD]**
[4294674.594000] hdb: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache
[4294674.594000] Uniform CD-ROM driver Revision: 3.20
```

So, my questions (I **do** have something to ask) are two-fold.

[LIST]
[*]Why did my old Mandrake 7.2 installation deal with this EZ-Drive/Disk Manager thing transparently, and my new Ubuntu 5.10 didn't? The kernel apparently detects it as [EZD].
[*]How can I extract a partition from an image of an entire drive, preferably into one monolithic file?
[/LIST]

Thanks in advance!

---

