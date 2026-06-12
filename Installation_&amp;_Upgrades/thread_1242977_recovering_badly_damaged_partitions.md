---
title: "recovering badly damaged partitions"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by michael37 on 2009-08-17
This is a fairly complex technical question about recovery of maliciously damaged partition table and file systems.

My laptop was configured to dual-boot Ubuntu and Windows. Windows partition was formatted under NTFS and was fully accessible (read/write) from Ubuntu using ntfs-3g.  Linux partition was formatted as ext-3 and not accessible from Windows.

Someone intentionally damaged my partition table and possibly data on the Windows partition.  The Windows partition now shows up as FAT32 in fdisk.  I am able to mount this partition as vfat, but the FAT and the data shows up badly garbled.  I suspect the label is wrong, but the real data underneath is still original NTFS.

Ubuntu partition was damaged too, but I was able to largely recover it.  The computer now boots into Jaunty with no problems.

Question: which tools are available in Linux to dig inside a broken NTFS partition?  I will likely need to manually find and identify Master File Tables and the rest of the NTFS metafiles.  I am fairly comfortable with what I am doing around file systems, so no worries about damaging it more than it already is.

Thanks in advance for help.

---

### Post by jerrrys on 2009-08-17
never had to use it, but sounds like what your looking for

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by michael37 on 2009-08-17
> **jerrrys said:**
> never had to use it, but sounds like what your looking for

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Never heard of this tool, but I'll give a try.
It sounds like a good idea might be backing up the damaged partition first (dd if=/dev/sda2 of=some_file_on_usb_drive) just in case...

---

### Post by jerrrys on 2009-08-17
an old timer (of linux) posted it a while back and i added to my database....

---

### Post by michael37 on 2009-08-19
Worked!! I was able to recover data with minimal data loss.  Testdisk scanned file allocation tables and found all the overlapping partitions.  All I had to do is to point it to the right ones... and both operating systems came up after a reboot.  However that rogue FAT32 was formatted, apparently it didn't significantly disrupt the underlying data structures.

---

### Post by jerrrys on 2009-08-20
:)

---

