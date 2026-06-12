---
title: "hardware detection takes forever with particular hard drive in system"
date: 2006-03-30
forum: Hardware &amp; Laptops
---

### Post by Jimmy The Clown on 2006-03-30
Weird problem here. There is a particular 300gb seagate drive with a single ntfs partition that seems to befuddle the way linux handles disks. When a livecd boots up, including ubuntu and others, it stalls for quite a long time after the "uncompressing linux kernel... booting the kernel line". Stalls for probably a good couple minutes. I got another surprise in the form of a several minute stall when the dapper installer was trying to find disks. After a while of waiting, the script finished without finding anything. It even seems to slow down the windows boot process by a minute or so. If I pull the drive out of the machine everything runs fine with the other hard drive in place.

I've tried every utility I can think of. Checkdisk found no errors in the partition. Partition managers report no problems.

I think this _might_ have started after I used the disk to migrate my GF to a new install. Something happen and the partition disappearred. I later recovered the partition using the acronis partition editor. However, I havent used the drive in awhile so I can't say thats what did it for sure.

The only error messages I have gotten have been generic about "timeout reading hdb" or sometimes an issue like "DMA not in use for hdb".

Anyone out there have any ideas??

-JTC

---

### Post by Joeb on 2006-03-30
It sounds like this drive is failing.  If you are getting timeout errors, most likely the drive is failing or it's not configured correctly in CMOS. In you CMOS settings, is it set for auto detection and is it detected correctly?

I would guess it's not a problem with the partition itself but the electronics on the drive.

---

