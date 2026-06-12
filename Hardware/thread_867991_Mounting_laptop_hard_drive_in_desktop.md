---
title: "Mounting laptop hard drive in desktop"
date: 2008-07-23
forum: Hardware
---

### Post by JC Denton on 2008-07-23
Hello All
I've recently purchased a IDE hard drive adapter much like this one:
[http://www.laptoprepair101.com/laptop/2006/02/16/connect-laptop-hard-drive-to-desktop-computer/](http://www.laptoprepair101.com/laptop/2006/02/16/connect-laptop-hard-drive-to-desktop-computer/)
to mount my laptop hard drive in my desktop machine. 
BIOS recognises the hard drive fine, reporting the correct drive size (40GB).
However, Ubuntu is unable to read from the drive (tested using fdisk /dev/sdd , cat /dev/sdd).
Also, in Computer: the drive shows up as scsi drive.  Clicking on the icon reports the same error - ubuntu is unable to read from it.

Thanks for your help.

---

### Post by phidia on 2008-07-23
Usually the linux system doesn't read a drive. It mounts a partition and depending on the file system reads that. 
"sdd" is a drive are there partitions on the drive? For example sdd1=1st partition on sdd.

---

### Post by coffeecat on 2008-07-23
Did that come from a Windows laptop with a hidden partition? Some manufacturers do weird things to the partition table. I had this issue with my Sony laptop when I tried to set it up as a multiboot. Suse was able to cope with the partition table, but not Ubuntu which reported the hard disc as being unformatted. (Strange - I can boot into Windows and Suse on this "unformatted" drive. :-k ) Every other distro I tried had the same problem as Ubuntu.

Eventually I reformatted the whole drive with Gparted, reinstalled Windows and all the Linux distros I wanted and here I am posting from Linux Mint from the self-same laptop.

If you have Gparted installed, see what that's telling you about the drive.

---

### Post by JC Denton on 2008-08-04
There are a couple of partitions on the drive (win,ubuntu, asus rescue partition) but these are obviously not recognised (only sdd in /dev/, no sdd#).
The intent is to recover the data from the partitions. I'll give booting from it a try..

---

