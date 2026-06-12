---
title: "Can't format LaCie 2TB external to ext3 file system, works with xp"
date: 2009-11-24
forum: Hardware
---

### Post by mocca007 on 2009-11-24
My goal is this:

Format the hard drive with EXT3 file system so that file ownerships can be maintained, this will be used as network storage for a few different people.


Here's my status:

I just bought a 2TB LaCie External hard drive, I tried many times in many ways to format it in ubuntu 9.04 with gparted with no luck.

I was able to partition it sucessfully in windows xp (shocking isn't it?) with no problems and it's now HPFS/NTFS.

I can mount and read/write data to the drive in ubuntu on the hpfs/ntfs partition with no problems.

When I go into gparted after formating to hpfs/ntfs with windows, it's showing this for the partitions:

/dev/sdb1      /!\      unknown        /media/disk     1.00KiB
unallocated             unallocated                           1.82TiB

the /!\ warning for /dev/sdb1 is showing this information:

Unable to detect file system! Possible reasons are:
-The file system is damaged
-The file system is unkonwn to GParted
-There is no file system available (unformatted)

When I try to make the 1.82TiB of unallocated space into an ext3 partition with gparted, it gives me this error:

"can't have overlapping partitions"


I thought it might be the partition table causing problems at first, but now that it's been successfully formatted in xp, I'm not so sure that's the issue.

What can I do to format this drive with the ext3 file system?

Thanks for all your help in advance! :)

---

### Post by i.r.id10t on 2009-11-24
Use fdisk from the command line

fdisk -l shows all partitions. Then fdisk /dev/sd?  (replace ? with whatever device your drive is using).  Delete all existing partitions, create a new one, exit, format.

---

### Post by mocca007 on 2009-11-24
I tried sudo fdisk /dev/sdb  and got this message:  

The number of cylinders for this disk is set to 243201. There is nothing wrong with that, but this is larger than 1024, and could in certain setups cause problems with:

 1) software that runs at boot time (e.g., old versions of LILO)
 2) booting and partitioning software from other OSs    (e.g., DOS FDISK, OS/2 FDISK)

could this have caused the problem with gparted?  (in the process of trying to format with fdisk now, will post results after)

---

### Post by mocca007 on 2009-11-24
after using fdisk,

sudo mkfs -t ext3 /dev/sdb1


this if what i am using to format the drive now, seems to be working so far :) I will post results.

---

### Post by mocca007 on 2009-11-24
Seems to work fine now with ext3 :)

odly enough, gparted still shows the same partition unallocated info when I look at the drive from there.

also when i look at the properties in nautilus it shows 93gb are in use, very strange......

any idea why that might be happening?

---

### Post by pakezonite on 2011-07-21
Hi!

Using GParted create a new partition table first 
-this will also remove the unknown partition.

After you can create whatever partitions / file systems
on your disk without errors.

-P-

---

### Post by Valezan on 2011-11-06
Hi,
 Firstly excuse my English.
 I plan to buy a “LaCie Wireless Space” and, following your example, I am going to format it in ext3 to backup the "home" folders with the owner's rights. But I wonder if, after having changed the partition format, the NAS maintains is functionality (I mean use it as a router, access point, or Ethernet/Wi-Fi extender as well as UpnP and DLNA compatibility)?
 Could you please inform me about this? Thank you in advance.

---

