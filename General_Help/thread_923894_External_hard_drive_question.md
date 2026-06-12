---
title: "External hard drive question"
date: 2008-09-18
forum: General Help
---

### Post by hatewindows on 2008-09-18
Hello all--I have a 80G USB 2.0 hard drive with some pictures and music that was loaded on a windows machine--When i plug the drive into my ubuntu pc-The drive is seen but i cant read anything when clicked--I get an error  about force mount and ntsf files...Is there a way to make this work easy? Thanks all and have a good night!!

---

### Post by zohaib on 2008-09-18
> **hatewindows said:**
> Hello all--I have a 80G USB 2.0 hard drive with some pictures and music that was loaded on a windows machine--When i plug the drive into my ubuntu pc-The drive is seen but i cant read anything when clicked--I get an error  about force mount and ntsf files...Is there a way to make this work easy? Thanks all and have a good night!!

Are You using NTFS drives?

---

### Post by hatewindows on 2008-09-18
Yes--The drive was formatted with a windows machine!  Can i change any of that while keeping the data on the drive?

---

### Post by zohaib on 2008-09-18
yea i had the same problem.,
but sure you can change it without loosing any data like I did.,

first install xp n put all the data from a drive to another drive n then formate that drive from which u have copied all the data to another drive., right click on the drive click format n then quick formate.,don't forget to put FAT32 in the box before clicking formate it's set to NTFS by default.,n formate the all drives respectively.
that's how I converted my NTFS drives to FAT32.,, it's a long process but that's what I've found easier.

that's all i can explain., since I live in Pakistan n our language is not english so my english is not good enough to explain little little things.

---

### Post by bubbalouie on 2008-09-18
The force thing usually means that the drive was not cleanly dismounted the last time windows used it, you may be able to plug it into a windows machine, read a file, then unmount (safely remove USB device). After this you should be able to mount it without having to specify the force option (I think).

If you do not have a Windows box handy (very understandable) try something like the following:

sudo mount -t ntfs-3g /dev/sda1 /media/sda1/ -o force,rw

Where /dev/sda1 is the USB drives main parition, and /media/sda1/ is a location that you have created to mount the drive to (this is going by memory sorry). Zohaib's suggestion is the solution to prevent this in future, FAT32 for all of its limitations is the best format to use as pretty much every computer you use will be able to work with it.

Good Luck

Ryan

---

### Post by mb_webguy on 2008-09-18
As long as the drive is shut down properly, you shouldn't have this problem.  I have a dual-boot with a shared data partition that's formatted as NTFS, and I've never had a problem with it.

With USB drives, you just have to make sure in Windows that you always, always, always use the icon in the system tray to safely remove the hardware.

---

### Post by scouser73 on 2008-09-19
> **hatewindows said:**
> Yes--The drive was formatted with a windows machine!  Can i change any of that while keeping the data on the drive?

Plug the HDD back into a windows machine, then you have to use the **Safely Remove Hardware** program, this will fix the problem for you, no messing about with anything really.

---

### Post by hatewindows on 2008-09-19
Wow--You guys are good..  Did the replug into windows (YUK) machine--shut the drive down correctly and bingo UBUNTU reads it great!!  Thanks all!!!!!!!!!    Have a great day!                MARK

---

