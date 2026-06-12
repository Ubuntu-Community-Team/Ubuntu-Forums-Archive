---
title: "Adding 3ware Raid-0 to Ubuntu 6.06"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by Duracell on 2007-05-18
I'll tell you what I intend to do, and I'll accept any advice on how to accomplish it - or how I should do it differently.

I'm configuring a fresh Ubuntu 6.06 Server to run JFFNMS for monitoring my small ISP's fiber-optic and fixed-wireless network. With the size of our network we're within spec to run the poller and DB on the same box. After finding the Nforce4 quasi-software RAID on our new Tyan board isn't going to give me Raid-5 in linux, I went in search of a controller. I ended up with a 3ware 9650SE. Downside - only supports two drives. I have four (320GB SATA-II). So, I figured I'd RAID-1 a pair off the onboard controller for the OS, and RAID-0 a pair with the 3ware for a high performance /var. Maybe that doesn't make sense, but that's how I worked it out in my head. Open for suggestions...

Moving on. I have Ubuntu running on the RAID-1 and now I'm not sure what do to format this 3ware. I have the RAID-0 configured in the 3ware BIOS, but I'm not sure how to get it installed from here - formatted and mounted as /var. The instructions I have from the 3ware driver package doesn't seem applicable, but I just don't know. ([http://www.3ware.com/KB/article.aspx?id=15102](http://www.3ware.com/KB/article.aspx?id=15102))

Thanks for the pointers!

---

### Post by bsmith1051 on 2007-06-22
Sorry no one's responded, and I'm not able to help either.  But I'm curious which method you used to install Ubuntu in RAID-1 on the Nvidia fake-raid?

---

### Post by bikeman1 on 2007-06-22
- the easiest solution to mount 4 drives is to acquire the 4-drive version of the 9650........

- I have had poor luck with using software raid with  on-board SATA  ports.  Lots of disk errors.  I was using a Gigabyte motherboard K8N51GMF-9.  I don't think this solution is nearly as robust or secure as the 3ware hardware RAID.  Maybe it will improve if there starts to be kernel support for the on board RAID of these chips.  Last I checked, it was not picked up by the kernel.  Maybe that has changed.  Even if it has, I would be leery of the reliability of these ports.  I lost two SATA drives using these for backup drives

- to format the 3ware array, just install and create the array in the 3ware  BIOS manager as the computer boots.  I think it supports raid 0,5, and 10 only.  Raid 5 is most secure but you get a much larger array with 4 disks than with 2 -- hence the suggestion that you need a larger card.

-after the array is created, Ubuntu should see the array as a single sda device.  So create a partition

fdisk /dev/sda

in fdisk, add a partition and write the partition table.  Select  the #1 primary partition.  Commands are detailed by typing "m".

then, create an ext3 file system

mke2fs -t ext3 -v /dev/sda1 

and your RAID will be formatted.

To mount the array, create a folder in /mnt (say, dog)

mkdir /mnt/dog
mount /dev/sda1 /mnt/dog

you can modify your fstab to automount the array in this folder

I think it would be a lot of hassle to create 2 separate arrays on different SATA ports, plus you will lose lots of disk space by using 2 arrays  if you elect RAID5 for security.  There are a lot of reasons to spring for the bigger card.

Hope this helps.  :D

---

