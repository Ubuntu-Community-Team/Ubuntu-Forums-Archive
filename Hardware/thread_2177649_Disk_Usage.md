---
title: "Disk Usage"
date: 2013-09-29
forum: Hardware
---

### Post by GrumpyBum on 2013-09-29
Hay all, hope everyone is having a good day.
Not sure where to post this but I wanted to get some feelers out there.

I am looking to balance the disk performance of my Ubuntu installation.
This is for an old laptop with 2 hard drives, a 60GB SSD and a 320GB SATA.
Basically, I want the storage but also the performance.

So I am wanting to install Ubuntu LTS 12.04 x64 Edition across the 2 disks.
The idea been that active / in use data is running off the SSD and data I am not currently using is automatically archived to the SATA.
Another way to look at this is I want to used the SSD as a cache to the SATA Disk providing me the full 320GB storage but the performance of the SSD.

Has anyone done this before? I would love to hear from you :)

This laptop will be running NetBeans as a primary point but additionally I have a Windows XP System in VMware Player that will also run off this laptop.

Thanks in advance, any articles / how too's / idea's will be appreciated.

---

### Post by Silux92 on 2013-09-29
Welcome!
I'd suggest to use as boot loader a partition in the SSD, and mount the SATA just after the boot.
Once mounted the SATA you can swap files as if they are on the same disk.
I'm using a 60GB ssd and a 180GB SATA right now.
If you are using a laptop you can use also a SD card as boot loader or a fast usb drive:)

---

### Post by GrumpyBum on 2013-10-02
Thanks Silux92,

I am going to give this ago but most likely over the weekend as higher priority work has come up.
I will get back to this post to let you know how this works out.

Thanks again,

---

### Post by oldfred on 2013-10-02
I have a 64GB SSD and 640GB hard drive plus a couple of old drives.
On my SSD I have two / (root) partitions, one is 12.04 as my working install and the second is for testing or future install. I also have test installs on hard drive. 
Hard drive has two data partitions of 100GB. One is NTFS for when I still booted XP from my old drive. I have not moved data to my Linux formatted data partition.

I have been hoping to build a new UEFI system so I used gpt partitioning and included an efi partition at beginning of drive even though I boot with BIOS now.

```
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  316MB   315MB   fat32                 boot
 2      316MB   317MB   1049kB                        bios_grub
 3      317MB   30.2GB  29.9GB  ext4         Precise
 4      30.2GB  60.0GB  29.9GB  ext4         Quantal

```

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by GrumpyBum on 2013-10-09
The system is up and running great / better then expected, configured as follows

boot - SATA OCZ-VERTEX3 60GB SSD
swap - 10GB on OCZ
/ (root) - OCZ SSD
/home - HP SATA 320GB at 5400rpm

System is fast even when exceeding 3GB of installed RAM and using SWAP.
Storage meets requirements and the system is working well.

Note, this is a $40 Laptop of eBay. HP 6910p + a $8 Multibay Adapter for HDD + the SSD I had sitting in my room. A very happy outcome :)

---

