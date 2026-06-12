---
title: "MDADM Hardware Issue - Intel H87 Chipset"
date: 2013-10-20
forum: Hardware
---

### Post by renny2 on 2013-10-20
Hi

Having a very strange issue with a new build,

Just put together a new build as below and the issue I am having is very strange.

1       SilverStone  ST50F-ES 500W PSU 80+
1       G Skill 8G(2x4G) DDR3 1600Mhz PC12800(GS-F3-1600C9D-8GAO)
1       Fractal Design Node 304 Mini ITX/DTX Case USB3.0
1       Match Xtreme ES SLC 16G USB3.0 Flash Drive Read up to160MB/s Write up to160MB/
1       Asus H87I-PLUS 2xDDR3 PCI-E 6xSATA3 6xUSB3.0 DVI D-SUB HDMI GLAN
1       Intel Core i3 4130 LGA1150 CPU 3.4Ghz 3Mb Cache Haswell 
2       Western Digital RED WD30EFRX RED NAS- 3TB/INTELLIPOWER/DDR2/3.5

I have tried a few different versions of Ubuntu but have focused on 12.04 Server

When setting up raid with the 2x Western Digital RED drives with the default settings mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sda /dev/sdb
everything works correctly as it should and I put a file system on the /dev/md0 and mount it and it works fine.

As soon as the computer is restarted the superblocks are gone from the hard drives and it fails to mount via fstab.

If i try and assemble it says it cannot locate any superblocks on /dev/sda or /dev/sdb depending on which order I add them in mdadm --assemble /dev/md0 /dev/sda /dev/sdb

I can create the RAID again and it will work fine but every single restart the superblocks will be gone and the raid will not assemble.

I spent about 4-5 hours trying everything I could think of to get this working to no avail including all the different options in the BIOS related to SATA, IDE / AHCI / RAID modes and turning on and off all the features., and as a final step I was playing around with --metadata=0.9 during creation and viola everything works perfectly - the raid mounts properly after every restart and the superblocks are persistent.

Any Idea? or would it be acceptable to just leave it as 0.9 metadata?

It's a bit concerning that there is something wrong with the SATA controller.

Thanks for reading.

---

### Post by SaturnusDJ on 2013-10-20
Superblock physical positions differ between version.
Try with partitions on the array members. Make these partitions a little smaller than the devices maximum size. [Here]("http://ubuntuforums.org/showthread.php?t=2110658&p=12484473#post12484473") you can read why that's a good idea.

---

### Post by renny2 on 2013-10-21
Thank's for the reply.

That didn't really answer the question,

I have tried partitioning the two drives as 8300 and fd00 before joining them to the raid but don't see why I should have to shrink partition sizes as I also have these two exact drives setup similarly in a previous generation ITX motherboard (P8H77-I) and they work with 1.2 Metadata without an issue.

I get the point about replacing with another hard drive and limiting your choices but that will not be a problem as if a disk dies the entire storage will be broken as it's raid 0.

---

### Post by SaturnusDJ on 2013-10-21
If you have partitions, you should be working with sda1 and sdb1. That's not what I see in your first post.

---

### Post by renny2 on 2013-10-21
I would prefer not to have to use the partition route as I have no need for them for this setup.

I created partitions on the disks, tested them working and then joined the disks to a raid via /dev/sda /dev/sdb as this is what I have done for every other setup **successfully**

Could you explain why it would potentially not work on this motherboard instead of offering a workaround?

[SIZE=1]*Also, when using metadata 0.9 and attempting to "tune2fs -m 1" I get the following error "Couldn't find valid filesystem superblock."*[/SIZE]
Nevermind the above line, pointed the wrong location.

Thank you

---

### Post by SaturnusDJ on 2013-10-21
In the link I posted earlier you can read why slightly smaller partitions are a good idea.

So you created the partitions but don't use them? Maybe that's the cause of the problem.
Erase them with dd and try again.

---

