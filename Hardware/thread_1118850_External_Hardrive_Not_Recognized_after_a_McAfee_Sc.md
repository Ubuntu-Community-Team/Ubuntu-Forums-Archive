---
title: "External Hardrive Not Recognized after a McAfee Scan"
date: 2009-04-07
forum: Hardware
---

### Post by Loan_Refi on 2009-04-07
McAfee Scan has damaged or erased External Hard Drive (The Wind0ze OS responsible for the problem has been replaced)

Now

I have brought the external hard drive into Ubuntu 8.04 and I can see the external hard drive but can't mount it, I get this error;

Unable to mount location
Can't mount file

I have changed usb cables to make sure the usb cable is good which it is and I get the same error.

fdisk -l results;

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61d67c5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163927556096 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa14452c

Disk /dev/sdb doesn't contain a valid partition table

The last line from results "Disk /dev/sdb doesn't contain a valid partition table" is obviously the problem.

My laptop hardrive is the first Disk /dev/sda 60 GB

Does this means the hard drive is bad, crashed? There is data on the hard drive that I need to recover.

The external hard drive is a Maxtor One Touch usb/firewire purchased in 2003

Any help is appreciated. 
Thanks!

---

### Post by ddrichardson on 2009-04-08
cfdisk might be able to rebuid the partition table and photorec will get a fair chunk of your data.

---

### Post by Loan_Refi on 2009-04-09
Hi, I googled the 2 items you mentioned and this is where I am today;

$ sudo cfdisk /dev/sdb

$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 163.9 GB, 163927556096 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa044514

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?         327       73449   587355756+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?           1           1           0   80  Old Minix
Partition 2 does not end on cylinder boundary.
/dev/sdb3          153216      153245      230272    9  AIX bootable
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?          17         573     4461573    2  XENIX root
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

After just doing this check I moved onto Testdisk folloed prompts per Testdisk and since yesterday it started to Analyse cylinder.  This is where I am after 1 entire day;

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 163 GB / 152 GiB - CHS 19930 255 63
Analyse cylinder  3537/19929: 17%

at the bottom of the terminal screen it give me an option to "Stop".

Is this supposed to take days?  Am I doing the right thing here? 

I read the instructions here [http://www.linuxconfig.org/Cfdisk](http://www.linuxconfig.org/Cfdisk) but I afraid if I create a partition I would erase my data if there is any which is what I'm trying to recover.

Can you help me with some direction from here? I appreciate all your help.
Thanks!

---

### Post by ddrichardson on 2009-04-10
Can you run fsck on it?

---

### Post by Loan_Refi on 2009-04-10
Hi, I stopped what I was doing and tried fsck;
A)
$ sudo fsck /dev/sdb
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
B)
$ sudo e2fsck -b 8193 /dev/sdb
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?

I'm assuming I can't run fsck.

---

