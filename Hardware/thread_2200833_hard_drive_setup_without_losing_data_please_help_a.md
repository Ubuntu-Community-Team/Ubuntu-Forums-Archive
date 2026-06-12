---
title: "hard drive setup without losing data please help asap"
date: 2014-01-21
forum: Hardware
---

### Post by matthew_solberg on 2014-01-21
hi my external hard drive case broke and im attempting to install this into my tower. ive gotten as far as hooking everything up im just lost at the point of installing the hard drive cause at the moment it shows up in my disk management as unallocated and i cant access it. im afraid to go any further as i do not want to lose any data on the drive. if i use the simple volume wizard will this format my whole drive? and if so how can i setup my drive without losing the data? its a 1tb westren digital sata/32mb drive and i have important data that i can not lose on this please help!!

---

### Post by Mark Phelps on 2014-01-21
> if so how can i setup my drive without losing the data?

Basically -- you can't. The fact that the current partitions are not seen is a guarantee that any new partitioning is going to overwrite the data already on the drive.

You would have to first migrate off ALL the important data you want to keep before attempting any reformatting.

You didn't tell us whether the existing partitions are Windows format (NTFS) or Linux format (ext2/3/4) -- that's important because it's generally best to use data recovery tools that match the formatting scheme of the drive when trying to recover data.

---

### Post by oldfred on 2014-01-21
Is this an Ultrabook with small SSD using Intel SRT. That uses RAID which is not seen by installer until you remove hidden RAID data on drive. You can re-implement Intel SRT after install of Ubuntu to hard drive or install Ubuntu to SSD and have a fast Linux system (but no cache for Windows boot).

Backup even more critical with your configuration. 

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

### Post by matthew_solberg on 2014-01-21
its ntfs. and how can i get the data off the drive if i cant access the drive?

---

### Post by oldfred on 2014-01-21
Does BIOS see drive?

What does smart data say about drive. 
From Ubuntu use Disks or Disk utility, click on drive and review Smart Status.

It may need chkdsk, but that has to be run from Windows.

---

