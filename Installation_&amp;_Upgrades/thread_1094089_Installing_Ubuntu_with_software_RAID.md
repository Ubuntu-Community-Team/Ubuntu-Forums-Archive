---
title: "Installing Ubuntu with software RAID"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by soupmonster on 2009-03-12
Hi,

My housemate and I recently had a bad experience with Windows Server. His setup was as follows:

- Windows Server 2008
- 1 x 200 GB disk as OS partition
- 4 x 1 TB disks as a 3 TB logical volume with software raid
- Recent fast dual-core CPU (can't remember details)

Upon installation, he was informed that this setup would allow for failure of one of the drives; it could be swapped out with an identical drive, and the volume re-built as it was before. We had about 4 months of uninterrupted file storage, racking up about 2.5 TB of data on our software raid array.

Then, disaster happened. One of the drives failed, but when we swapped it out and ran the procedure to re-create the data, the whole array was wiped.

My question then, is this. Would a similar software raid setup be possible with an install of Ubuntu, and, if possible, advantageous? As a reasonably savvy user of Linux and Ubuntu in particular, is the swapping of broken drives possible, and is the procedure for restoring the array a simple one? Are there any easy-to-follow guides available?

If not... we are seriously considering a copy of Windows Home Server. Don't make us do it!

---

### Post by dstew on 2009-03-12
I created some software RAIDs on an old 4-disk NAS that worked great. I used an Ubuntu alternate install CD to create the RAIDs and install Ubuntu. I made a RAID1 for the boot system (grub cannot boot a striped RAID, but you can fool it with a mirrored RAID), and a RAID5 for the rest. I never tried to recover the RAID5 though, so I couldn't say if it would be easy or hard. You use the program [mdadm]("http://linux.die.net/man/8/mdadm") to manage the RAIDs, using the terminal.

---

### Post by miegiel on 2009-03-14
> **soupmonster said:**
> My question then, is this. Would a similar software raid setup be possible with an install of Ubuntu, and, if possible, advantageous? As a reasonably savvy user of Linux and Ubuntu in particular, is the swapping of broken drives possible, and is the procedure for restoring the array a simple one? Are there any easy-to-follow guides available?

I use debian for my server and ubuntu for my desktop, but that's just a personal choice. My raid(5) is in my ubuntu desktop. To be honest, I haven't tested rebuilding the array with a fresh disk. The best way is to test it. Just install linux on a spare pc with 4 disks, install the OS on one and build a raid 5 from the remaining disks. Fill the raid array with data, remove a disk, wipe the disk (on a other pc), put it back and see what happens :D

This way you also learn what you need to do when a drive fails once you have the server running.

```
sudo apt-get install mdadm
```

To install mdadm "A Linux utility ... that is used to manage software RAID devices".

some links to read more :
[http://en.wikipedia.org/wiki/Mdadm](http://en.wikipedia.org/wiki/Mdadm)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by soupmonster on 2009-03-20
Cheers, I found a useful [guide]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/"), which gives you an indication of what to do when a drive fails. Looks like you have to copy the partition table from one of the working drives, then use mdadm to load the disk back into the RAID.

Got my server all set up now, the 4 TB are now down to 3 TB with RAID 5, but everything seems to be running smoothly.

---

