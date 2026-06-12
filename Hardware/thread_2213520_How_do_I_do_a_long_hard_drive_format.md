---
title: "How do I do a long hard drive format?"
date: 2014-03-27
forum: Hardware
---

### Post by georgeward520-c on 2014-03-27
Before I re-install Ubuntu 13.10, how do I do a long hard drive format? I know you can use a LiveCD and use GParted to format your hard drive. What format should I put the hard drive in too? Thanks guys!

---

### Post by ajgreeny on 2014-03-27
You do not really need to format the disk before installing or re-installing ubuntu as the installer can do that at the time.  Is there some good reason for wanting to do this, eg some sensitive information and files on the disk that MUST be removed totyally before the disk is reused?

If so you can use utilities such as [DBAN]("http://www.dban.org/") which I think is often unnecessary for normal situations, but have a good look to see if it fits your needs.  You can also use **dd** at the command line but be very careful if you do that as its also known by some as "Disk Destroyer" because if you get the wrong device when you use it you might totally remove your OS.
See [http://ubuntuforums.org/showthread.php?t=1029849](http://ubuntuforums.org/showthread.php?t=1029849) for some detailed suggestions.

As for the format type, you must use a Linux filesystem in the installation such as ext4, but you do that in the installation process.  I personally recommend an ext4  root partition, /, of about 20GB, a swap of about 2GB unless you want to hibernate, when you need at least as much swap as you have ram, and the rest as /home partition.  There are many other partitioning ideas with, for example a shared ntfs data partition if you have a dual boot with windows, but come back for more info about that if you think it suits your situation.

---

### Post by tgalati4 on 2014-03-27
If you are reinstalling because you suspect some disk problems, then a low-level reformat may help.  Look for Ultimate Boot CD.  It contains a collection of manufacturer's utilities to diagnose the disk and perform a low-level format.  Otherwise ajgreeny's suggestions will work well.

---

### Post by SeijiSensei on 2014-03-27
You can use the badblocks utility to test the physical integrity of your hard drive.  Using the "-w" option will include both a writing and reading phase and will take hours.  From "man badblocks":
> 
-w     
Use write-mode test. With this option, badblocks scans for bad blocks by writing some  patterns  (0xaa,  0x55, 0xff, 0x00) on every block of the device, reading every block and comparing the contents. 


You can include an invocation of badblocks while formatting a disk with mke2fs.  Use "-c" for a read-only test, and "-cc" for the read-after-write version.  For instance,
```
mke2fs -c /dev/sdb1
```
will run a read-only test with badblocks then create an ext4 filesystem.  The format program will use the list of bad blocks generated from the scan, if any, and mark those blocks as unusable during formatting.

---

