---
title: "rescuing FAT32 partition &quot;Logical sector size is zero&quot;"
date: 2012-01-13
forum: Hardware
---

### Post by mistafeesh on 2012-01-13
Hi, I was in the process of resizing a FAT32 partition on an external hard drive with Gparted when something happened (not really sure what) and now it's not recognised.... 

Running dosfsck comes up with the error "Logical sector size is zero" and quits. If I check it i disk utility it says the partition is 'healthy' whatever that means....

Any ideas if it can be rescued?

---

### Post by oldfred on 2012-01-13
Post this:

sudo sfdisk -l -uS

Backup current partition table to another device just in case. If not sdb change to correct device.
sudo sfdisk -d /dev/sdb > parts.txt

And take a look with testdisk to see what it says, it may be able to revert to old partition table?

If not rebooted recover partition:
[http://ubuntuforums.org/showpost.php?p=10364557&postcount=34](http://ubuntuforums.org/showpost.php?p=10364557&postcount=34)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by mistafeesh on 2012-01-14
Ah thank you! Hadn't heard of testdisk but after reading your links, a bit of fiddling around with it got the partition restored.

---

### Post by oldfred on 2012-01-15
Glad it worked. You can post solved using thread tools.

---

### Post by mistafeesh on 2012-01-22
Hi, only just saw your post about marking it as solved...
I'm actually having some more trouble with the same HDD. Not sure if I should start a new thread for it?

My problem is that I can't just take everything off the disk and reformat it as I don't have enough storage. I've copied everything really important into various places but there's still about 250 gig on there that's currently not backed up so I'm a little scared to mess with it!

I managed to move this onto an ext4 partition but now both disk utility and gparted are refusing to create a fat32 partition on the drive.

I had the following error from testdisk but wasn't sure what to do about it:
> Warning: the current number of heads per cylinder is 255 but the correct value may be 128.

When trying to create the fat32 partition I had the following error from gparted:
> create new fat32 file system  00:04:05    ( ERROR )
    	
mkdosfs -F32 -v -n "media" /dev/sdb1
    	
mkdosfs 3.0.9 (31 Jan 2010)
/dev/sdb1 has 255 heads and 63 sectors per track,
logical sector size is 512,
using 0xf8 media descriptor, with 1480435712 sectors;
file system has 2 32-bit FATs and 32 sectors per cluster.
FAT size is 361280 sectors, and provides 46241035 clusters.
There are 32 reserved sectors.
Volume ID is 461b07dd, volume label media .
mkdosfs: failed whilst writing FAT

:confused:

---

### Post by oldfred on 2012-01-22
What setting do you have in BIOS. It should be LBA or large or large block allocation?
Does Disk Utility show Smart Status as ok?

Actually cylinders, heads, sectors have not been used since drives went over 8GB. So most drives default to 255 heads & 63 sectors per track with the number of sectors calculated to be the drive size. I often see strange heads & sectors on flash drives with FAT formats.

Why FAT32? It is fine for small flash devices. But it cannot store a file over 4GB and it does not have a journal so recovery is more difficult. IF you need compatibility with Windows NTFS is much better.

---

### Post by mistafeesh on 2012-01-22
Ah OK I didn't realise that stuff was irrelevant.
fat32 is just the lowest common denominator. It works on my housemate's old PC, my kids wii media player, my prehistoric G4 mac, my ubuntu box and pretty much anything else. I'm keeping an ext4 partition too for larger files, backups of important stuff etc though there's not too many of those.

Disk utility says SMART is 'not supported' It's a pretty new SATA drive in a cheapish USB2 enclosure. 

Not sure where to look for LBA info.

---

### Post by oldfred on 2012-01-22
I guess FAT is the common denominator across old Macs and some gaming devices.

Not familiar with errors on manual partitioning. I have always just used gparted since DOS days.

---

