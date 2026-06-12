---
title: "EXT3: Is there no hope?"
date: 2008-09-11
forum: General Help
---

### Post by database_dan on 2008-09-11
I was performing an install of Ubuntu, and in a flash of brilliance, I formatted my FAT32 partition (with all my personal, must have important files) to EXT3.

I see: [http://free-backup.info/data-recovery-software.htm](http://free-backup.info/data-recovery-software.htm)

But are there any data recovery programs in existence for my EXT situation (everything seems to be geared for NTFS or FAT)?

I know I know, I should have backed up all my 0 and 1's.
~Dan :(
(I have learned so much from my mistakes, that I am thinking about making a few more.)

---

### Post by -Zeus- on 2008-09-11
I highly doubt you could recover a formatted partition.

---

### Post by Vivaldi Gloria on 2008-09-11
Trying bodhi.zazen's suggestions here wouldn't hurt:

[http://ubuntuforums.org/showthread.php?t=915931](http://ubuntuforums.org/showthread.php?t=915931)

---

### Post by mb_webguy on 2008-09-11
If you haven't written anything to that partition yet, you *should* be able to recover *something* using TestDisk or something similar, but it's going to be slow work.

If you've written any data to the partition, you're pretty much out of luck.  You might be able to get some partials files, or maybe a handful of small files, but probably not much of any use.

---

### Post by unutbu on 2008-09-11
First thing to do is to unmount the partition, so the operating system does not write over your data.

Next, clone the partition with Partimage ([http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)). Do all your recovery work from the cloned partition. You could skip this step -- it depends on how serious you are about recovering everything possible. By cloning the partition you can make several attempts at data recovery. Without backing up first, using a tool like TestDisk will alter the partition, making it more difficult to return  to your current state if the need arises.

Then try TestDisk. It can search the partition for backup copies of the FAT32 filesystem and can possibly restore the old filesystem using the backup FAT.

To install TestDisk:
```

sudo apt-get install testdisk 
```

(or use Synaptic).

Here is the TestDisk homepage: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Here is a guide on using TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
Here is good general info on data recovery: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

If TestDisk can not recover your FAT32 filesystem, then read about the data carving  tools here:
[https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image](https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image)

PhotoRec is a popular data carving tool, which, despite its name, can search the partition bit-by-bit to recover of many different types of files (not just images). PhotoRec is mentioned in the above link, and comes with TestDisk.

Good luck.

---

