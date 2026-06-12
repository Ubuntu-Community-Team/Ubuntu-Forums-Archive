---
title: "hdd Problem?"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by Dr.Bunshin on 2007-03-13
Hey Community

It takes almost 20 minutes to boot my system, something to do with hdd. 

```

[17179574.216000] Probing IDE interface ide1...
[17179574.952000] hdc: TSSTcorpDVD-ROM TS-H352A, ATAPI CD/DVD-ROM drive
[17179575.120000] hdd: probing with STATUS(0x7f) instead of ALTSTATUS(0x50)
[17179575.288000] hdd: probing with STATUS(0x7f) instead of ALTSTATUS(0x51)
[17179575.624000] hdd: probing with STATUS(0x7f) instead of ALTSTATUS(0x51)
[17179575.736000] hdd: TSSTcorpCD-R/RW TS-H292A, ATAPI CD/DVD-ROM drive
[17179575.796000] ide1 at 0x170-0x177,0x376 on irq 15
[17179605.796000] hdd: lost interrupt
[17179605.796000] hdd: task_in_intr: status=0x7f { DriveReady DeviceFault SeekComplete DataRequest CorrectedError Index Error }
[17179605.796000] hdd: task_in_intr: error=0x00 { }
[17179605.796000] ide: failed opcode was: 0xa1
[17179605.808000] hda: max request size: 512KiB
[17179605.832000] hda: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[17179605.832000] hda: cache flushes supported
[17179605.832000]  hda: hda1 hda2 hda3 hda4
[17179605.868000] hdc: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179605.868000] Uniform CD-ROM driver Revision: 3.20
[17179606.092000] hdd: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[17179606.092000] ide: failed opcode was: unknown
[17179606.092000] hdd: drive not ready for command
[17179606.092000] hdd: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[17179606.092000] ide: failed opcode was: unknown
[17179606.092000] hdd: drive not ready for command
[17179606.092000] hdd: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[17179606.092000] ide: failed opcode was: unknown
[17179606.092000] hdd: drive not ready for command
[17179606.092000] hdd: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[17179606.092000] ide: failed opcode was: unknown
[17179606.092000] hdd: DMA disabled
[17179606.092000] hdd: drive not ready for command
[17179606.140000] hdd: ATAPI reset complete
[17179611.140000] ide-cd: cmd 0x5a timed out
[17179611.140000] hdd: lost interrupt
[17179616.144000] ide-cd: cmd 0x5a timed out
[17179616.144000] hdd: lost interrupt
[17179616.144000] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17179616.144000] hdd: packet command error: error=0xb4 { AbortedCommand LastFailedSense=0x0b }
[17179616.144000] ide: failed opcode was: unknown
[17179676.144000] ide-cd: cmd 0x3 timed out
[17179676.144000] hdd: lost interrupt
[17179676.144000] hdd: request sense failure: status=0x51 { DriveReady SeekComplete Error }
[17179676.144000] hdd: request sense failure: error=0xb4 { AbortedCommand LastFailedSense=0x0b }
```

Is that my CD drive? How can I fix this.

---

### Post by apjone on 2007-03-13
disable your cd drive in the BIOS and try to boot, see if that makes a differance. If so then yes it is your cdrom drive.

---

### Post by xyz on 2007-03-13
Those lines you posted drove me nuts about 8 months ago. HD was dead!
*Only speaking from my own experience.*
How about your data on the drive? Used a live cd?

---

### Post by xyz on 2007-03-13
You may want to have a look at the thread I started back in June 06:
[ Is my HD dead?]("http://ubuntuforums.org/showthread.php?t=206742")
It's quite long; there are also some suggestions/ideas/links that may work for you.
Let me know and good luck.

---

### Post by xyz on 2007-03-13
I can't remember  who posted this but here it it using GParted Boot CD or a Live CD so long as you become root and know if partitions are in FAT 32, ext3 or whatever.
> Using Gparted:
Running a filesystem check on a FAT32  filesystem

  root@GParted:~# fsck.vfat -a -l -v /dev/hda1 (change 1)
  
  
Running a filesystem check on an ext3  filesystem
(Website under construction, not much here yet....)
Code:

  root@GParted:~# e2fsck -C0 -p -f -v /dev/hda2

Where: hda2 is the ext3 partition to be checked. This command works very well.

  root@GParted:~# e2fsck -c -c -v /dev/hda2

This one is more for coping with bad blocks in your hard disk.

mke2fs is the command used to make an ext2 filesystem in a device.

tune2fs is the ext2 or ext3 tuning program.

dumpe2fs shows information from the superblock. 'sudo dumpe2fs -h /dev/hda2' shows the information that is in the superblock of /dev/hda2.


---

### Post by Dr.Bunshin on 2007-03-13
Hey xyz

Ok, looking at that thread. But my cd drive works fine... or does it. i think your right, i had some problems with it in vindows also. Seems perfectly reasonable and I am restarting to disable the it. I have two and I need them both for stuff. Do you know of anyway to fix it though? It seems to work fine once I am booted. :confused:

---

### Post by xyz on 2007-03-14
Try to chk disk with a Live CD, using the command lines I posted.

If I remember it right, it eventually booted despite those lines you posted but, sooner or later, it didn't anymore.

---

### Post by Kinslayer on 2007-04-16
I had a problem with long startup & shutdown times.  The problem was my cd rom & dvd rom weren't mounting properly.  They were attached to the same ide cable.  How I fixed it was I shutdown the system, unplugged the cables from each, & rebooted.  It started right up.  Aha.  I shutdown again, which took less than a minute instead of the usual 5-10 minutes.  I connected one drive, started up, & it loaded quickly.  I repeated this with the second drive, with no problems.  A third time with both booted up quickly, and it hasn't been an issue since, at least for the couple of days since I've done this.

---

