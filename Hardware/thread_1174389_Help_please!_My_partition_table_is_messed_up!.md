---
title: "Help please! My partition table is messed up!"
date: 2009-05-30
forum: Hardware
---

### Post by audiochronic on 2009-05-30
I have a dual boot laptop with windows xp and ubuntu 9.04. I could not access my linux partition from windows anymore after converting to Jaunty and using ext4. I fiddled with some settings in the ext2fs program to try and see the partition. Next time i rebooted my laptop I got Grub error 17. 

I originally had a 
- 130Gb ntfs partition with xp installed
- 130GB linux partition with ubuntu installed
and a 40 GB ntfst partition has random files. 

From a live cd i can mount the linux partition and /dev/sda6 which is a 40 gb ntfs partition but not the windows partition. 

I have attached a screenshot of  gparted. My windows partition was around 130 GB it looks like the used part of the partition is seens as a 50 gb drive (/dev/sda5) and the unused part is listed as unallocated. 

Please help me on how to make the windows partition mountable again ( i have been able find the windows partition through testdisk and list the contents so i know the data is still there). Also how do i reinstall GRUB so i can boot into something again. 

Any help most appreciated.   


fdisk -i output 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00094b60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             192       22359   178061656+   f  W95 Ext'd (LBA)
/dev/sda2   *       22360       38519   129805200   83  Linux
/dev/sda5             192        6606    51520455    7  HPFS/NTFS
/dev/sda6           17201       22359    41439604+   7  HPFS/NTFS

testdisk output

 1 E extended LBA           191  89  1 22358 254 63  356123313
 2 * Linux                22359   0  1 38518 254 63  259610400
 5 L HPFS - NTFS            191  89 27  6605  89 26  103040910
   X extended             17200   1  1 22358 254 63   82879272
 6 L HPFS - NTFS          17200   2  1 22358 254 63   82879209 [VMS]

---

