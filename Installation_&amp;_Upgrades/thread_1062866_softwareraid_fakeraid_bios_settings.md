---
title: "softwareraid fakeraid bios settings"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by mihe on 2009-02-07
Hi, I plan to install ubuntu 8.04 or 8.10 on a amd64 Opteron machine. Im a newbee to linux so hopefully this is a simple question. 
As far as I understand there are three types of raids: Hardware, Software and Fakeraid (=hardware and software combined). I have Fakeraid hardware and two sata harddisk. I want to install raid0 for increased speed during numerical computations.
I have understod that if I use the ubuntu alternate Install I can install either software or fakeraid. 
On [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) it says that the only advantage of fakeraid compared to software raid is in case I want dual boot. I dont want dual boot hence software raid is reccomended for me (“it is better to use the standard Linux drivers”).
I have two questions:

1. If I install Software raid should I then disable raid in the bios?

2. On [http://reformedmusings.wordpress.com/2008/12/27/ubuntu-810-intrepid-and-nvidia-raid/](http://reformedmusings.wordpress.com/2008/12/27/ubuntu-810-intrepid-and-nvidia-raid/) it says “At the other end of the spectrum is software RAID which requires no special hardware”.
If software raid requires no special hardware, then (since raid0 is faster) why is not all file systems installed with raid0?

Kind regards,
Micke

---

### Post by peter72 on 2009-02-07
> 1. If I install Software raid should I then disable raid in the bios?

2. On [http://reformedmusings.wordpress.com...d-nvidia-raid/](http://reformedmusings.wordpress.com...d-nvidia-raid/) it says “At the other end of the spectrum is software RAID which requires no special hardware”.
If software raid requires no special hardware, then (since raid0 is faster) why is not all file systems installed with raid0?

1.  Yes, you should disable RAID in the bios.  This will speed up your boot time a lot.

2. RAID 0 is a stripe across 2 or more disks and is faster on both reads and writes, but non-redundant, so if you lose one disk you lose all your data.  RAID 1 is a mirror across 2 disks,  RAID 1 can be faster on reads, but the same speed on writes.  The advantage of RAID 1 is that you can lose a disk and not lose your data.

We won't go into RAID 3/4 or 5, as they're intended for 3+ disks.

Here's a howto to get software RAID with ubuntu.

[http://ubuntuforums.org/showthread.php?t=408461 ]("http://ubuntuforums.org/showthread.php?t=408461")

---

### Post by mihe on 2009-02-07
Thank you!

---

### Post by alanwalterthomas on 2009-03-20
I'm another noob with a fakeRAID mobo. I wanted RAID0 too boost performance (& I have what little is important on a couple DVDs so no need to mention risk) & became dismayed when I found out about the fakeRAID. High-end RAID cards are out of the question & I'd probably be better of upgrading the CPU anyway. However, I have a reasonably modern dual core processor & I think Linux's built in softRAID (mdadm?) should do the trick.

However, I wanted the RAID0 along with ext4 in 9.04 for that lightning fast boot, but since it's not hardware I'm not sure how much the RAID0 would speed up the boot sequence. I'm thinking I might actually slow down the system if it has to start drivers, figure out what to do with the RAID, etc. So, would softRAID0 be worth anything in terms of fast boot, or only useful once the OS is mostly loaded?

Also, I have a really old 32 MB 8x CF card that I was thinking about using as the /boot partition (needs to be separate for softRAID right?). /boot on my current machine only occupies about 23 MB so it should fit. I think 8x = 1.2 MB/s which is quite slow, but since GRUB is only a couple hundred KB anyway, I thought it might equal or even beat the HDD in quickly getting a couple little files out.

thanks for any comments

---

