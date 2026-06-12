---
title: "format 3tb drive with gpt and NTFS so it works in win7 and win10?"
date: 2017-11-16
forum: Hardware
---

### Post by sdowney717 on 2017-11-16
I cant get the 3tb drive to work in either OS, it will only partiton and format for 7 or 10.

win7 has the 2TB limit, so has to be formatted gpt. Then works fine. But putting that drive in win10, win 10 cant use the partition made by win7 at all. It has to be cleaned with diskpart and setup as gpt in win10, AND then it wont work in win7.

So was wondering if gparted can make it work for both OS.

It worked, I used livemint usb. It partitioned as gpt, then I selected ntfs. Works in win10 and win7.

The windows partitoner could not make it work.

---

### Post by oldfred on 2017-11-16
Both Windows 7 & Windows 10 work with gpt. 
You can even install Windows 7 in UEFI mode, but DVD is only BIOS/MBR. It has to be copied to flash drive and some files renamed & moved to make it UEFI bootable.

You may just be having the fast start up or hibernation issue. Windows 10 is always hibernated and then no other system can see/use in read/write mode all NTFS partitions.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If 3TB drive you need to use gpt.

---

### Post by sdowney717 on 2017-11-17
> **oldfred said:**
> Both Windows 7 & Windows 10 work with gpt. 
You can even install Windows 7 in UEFI mode, but DVD is only BIOS/MBR. It has to be copied to flash drive and some files renamed & moved to make it UEFI bootable.

You may just be having the fast start up or hibernation issue. Windows 10 is always hibernated and then no other system can see/use in read/write mode all NTFS partitions.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If 3TB drive you need to use gpt.
Yes it was partitioned gpt in win7.
I almost gave up getting it to work in both 7 and 10.

Windows 7 and 10 gave me so much grief about that drive, gparted made it work fine. The gparted engineers know their stuff.
I have a link here with lots of pics and discussion about what I went through.
Some of those guys did not believe me or they are just MS fan boys.
IMO, there is a bug in win10 when it cant recognize a drive partitioned in win7.


[https://www.tenforums.com/drivers-hardware/98138-3tb-drive-works-win7-win-10-no.html](https://www.tenforums.com/drivers-hardware/98138-3tb-drive-works-win7-win-10-no.html)

---

### Post by oldfred on 2017-11-17
Is this in an old drive adapter?
We have seen various issues with external drive cases/adapters. Some do not seem to work with gpt at all. Some do not like larger drives.

post this:
sudo parted -l
sudo gdisk -l /dev/sdX  #where X is 3TB drive.

---

### Post by sdowney717 on 2017-11-17
> **oldfred said:**
> Is this in an old drive adapter?
We have seen various issues with external drive cases/adapters. Some do not seem to work with gpt at all. Some do not like larger drives.

post this:
sudo parted -l
sudo gdisk -l /dev/sdX  #where X is 3TB drive.

Older, well it is a legacy bios, AMD Phenom 9650 Aspen HP motherboard with AMD 780G chipset.
I can do it some day, I dont normally run ubuntu on that PC.

---

### Post by oldfred on 2017-11-17
If drive is internal you need to make sure AHCI mode is on, if you have it, not IDE nor RAID.
But if external drive, I do not think that matters.

---

