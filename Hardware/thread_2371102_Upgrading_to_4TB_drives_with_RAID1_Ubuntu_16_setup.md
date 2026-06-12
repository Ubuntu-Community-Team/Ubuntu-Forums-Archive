---
title: "Upgrading to 4TB drives with RAID1 Ubuntu 16 setup"
date: 2017-09-10
forum: Hardware
---

### Post by technobabble2 on 2017-09-10
I've been digging around on the forum for days and getting tons of conflicting information.  I'm hopelessly lost. 

My ultimate goal is to replace the 2 existing drives in the RAID1 array with the new 4TB hard drives and retain the current setup so I don't have to go through the long hours of setting the server up again.  

As stated in the topic, I have a basic Ubuntu 16.04LTS server set up.  No dual boot or anything unusual.  I have 2 HDDs on a RAID1 setup. 
One is a 750GiB and the other a 1000GiB.    

I have an 8GiB Swap on /dev/sd[ab]1 and.. 
the / is the max size Ubuntu said would fit on /dev/sd[ab]2 (the exact size doesn't really matter at this point, but you can see it below)      

cat /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md125 : active raid1 sda2[1] sdb2[0]
      724630528 blocks super 1.2 [2/2] [UU]
      bitmap: 0/6 pages [0KB], 65536KB chunk

In this setup everything works and boots as normal.  

The first thing I tried was to just dd the smaller of the 2 drives over to my new 4TB drives and add them to the array.  That worked great and I could expand them to 2TB once i took sda and sdb drives out.  If I tried to expand them to the full 4TB size it started getting into GPT stuff and would no longer boot.    

I've tried wiping the drives and using gdisk to create >2TB partitions but I run into the boot issues. 

 I have an ASUS A68HM-K and it definitely has UEFI capabilities and they're turned on.    This is clearly an issue of me not knowing what I'm doing or where to start.  Does anyone have a link to a tutorial on this sort of thing?  Is it better to dd an exact copy and expand them later?  Or make the full size partitions and rsync a copy over?

---

### Post by oldfred on 2017-09-11
I do not know RAID nor details of configuration.
But for booting.
But UEFI does not have RAID drivers, so the ESP must be outside of the RAID.
You then need a separate FAT32 partition with boot flag to make it the ESP.

You have to use gpt if you want support for more than 2TiB. 
You can still use BIOS boot if you have to with gpt, but then need a bios_grub partition of 1 or 2MB unformatted with bios_grub flag if using gparted or ef02 code if creating with gdisk.

If you create MBR drive, you can possibly convert to gpt, but ESP is recommended to be first partition or near start of drive.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

But you can get into the issue of changes to UUIDs and major editing of fstab & reinstall of grub.

As I suggest to Desktop users, better to just do a new clean install to correctly partitioned drive.
I might suggest both the ESP & bios_grub as first two partitions then add the partitions you want or in effect now have. Then copy all your data from old RAID to new RAID partition(s).

This process should be no different than if you had a major failure & had to do a new install & restore all your data.
       
 Best pratice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)

---

### Post by technobabble2 on 2017-09-11
Thanks for the reply, I'll get started on this right now.

---

