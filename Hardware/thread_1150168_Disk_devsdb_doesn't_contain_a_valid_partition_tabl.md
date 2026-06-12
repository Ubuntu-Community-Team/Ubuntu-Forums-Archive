---
title: "Disk /dev/sdb doesn't contain a valid partition table"
date: 2009-05-05
forum: Hardware
---

### Post by yawnmoth on 2009-05-05
I plugged a hard drive into my computer via a USB<->ATA adapter and am having trouble accessing its contents.  When I do "sudo fdisk -l" I get the following:

```
Disk /dev/sdb: 30.0 GB, 30005821440 bytes
64 heads, 32 sectors/track, 28615 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```
Is there a way to repair damaged partition tables or am I just going to have to forget about the data, delete the partition, and create a new one?

---

### Post by caljohnsmith on 2009-05-06
Can you give any more information, like were you previously able to access the partition(s) on that HDD, and if so, how many partitions did you have? Do you know what you did that might have deleted/corrupted the partition table? 

You can try recovering the partition table on that HDD using "testdisk"; to use testdisk, how about downloading the [testdisk-6.11.1.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the sdb HDD and then "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be the partitions you want to recover. We can work from there if you want.

John

---

