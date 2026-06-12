---
title: "Can I copy my Win Data to a new Disk?"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by mibadt on 2008-01-22
Hi,
I have a dual boot (XP/Kubuntu) system on a singe SATA HD.
My XP/SP2  has 2 NTFS partitions ( A C "system", and an E "data").
I have ran out of space on my C partition (I have space left on other partitions).
I intend to buy a new HD for my XP.
my questions:
1. All current HD are SATA 2 whereas my current HD is SATA (1 ?). IS SATA 2 compatible with SATA (I have a 3-4 years old Gigabyte motherboard with 2 GB RAM).
2. Can I simple connect the new SATA 2 drive to the empty MB SATA cable.

If YES, is the following logical:
a. Boot from KNopix 
b. Use Qpartd to partition the new HD
3. use dd to copy my "old" C & E partitions to the (larger) new ones.


Is thee a better way?

Thanks a lot upfront !

Best regards,

Michael Badt

---

### Post by Existentialist on 2008-01-25
SATA2 is supposed to be backward compatible with SATA1 controllers and you should not see any real difference in performance.  Some SATA1 controllers had issues with SATA2 devices, but this can almost always be corrected by setting a jumper on the HD to force it to run in SATA1 mode.

As for copying the data, your method should work, but I am not sure windows will run off of the new drive simply by copying over the old system files without the MBR.  I would consider copying over files you wish to keep, and combine your C and E partitions to make a larger system partition on the old drive.  Keep your data on the new drive separate from your system drive.

An easier method may be to install the new HD and boot in to Kubuntu to do the formating of the new drive and copying files.  There is no need for a live cd if you already have a working install.

---

