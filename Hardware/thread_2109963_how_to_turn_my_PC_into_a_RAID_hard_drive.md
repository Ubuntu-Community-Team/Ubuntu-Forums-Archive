---
title: "how to turn my PC into a RAID hard drive"
date: 2013-01-29
forum: Hardware
---

### Post by anorphirith on 2013-01-29
Hi, I'm new at linux and very excited to learn more ! 
I have a small project in mind and I need direction on how to proceed and look for more informations.

What I have:
-mini ITX motherboard with 2 (USB 3) and 3 (SATA) inputs
- gigabit ethernet input
-3 (2TB hard drives 3.5")
-a wifi dongle
-ubuntu :guitar:

What I want to do:
-have linux installed in raid 5 OR operate the drives in raid 5 
-when I plug my laptop into one of the USB inputs it would behave just like an external hard drive
-be able to access the drive with the ethernet input
-be able to access the drive as if it were an FTP server 

Thanks in advance ! :)

---

### Post by SaturnusDJ on 2013-01-29
For raid5 google at 'mdadm raid5.'
When using an Ubuntu alternate installer (<12.04) you can configure the array during install. The newer versions (desktop only because alternate is cancelled) have a different method that I haven't used yet.

Edit:
Just checked it out. No raid options found in the 12.10 desktop installer.
I suggest using the 12.04 alternate, it's pretty easy configuring raid with internet tutorial.

---

### Post by craigcrawford114 on 2013-01-29
I once had to migrate a server from a single disk to a RAID 1 array. Afterwards, I wrote a guide to help others so this may help you for the RAID bit (that is assuming you already have Ubuntu installed).

[http://ubuntuforums.org/showpost.php?p=10955299&postcount=9](http://ubuntuforums.org/showpost.php?p=10955299&postcount=9)

Though that was a guide for an older version of Ubuntu, and for RAID 1 so YMMV.

---

### Post by Fafler on 2013-01-29
> **anorphirith said:**
> 
What I want to do:
-have linux installed in raid 5 OR operate the drives in raid 5 
-when I plug my laptop into one of the USB inputs it would behave just like an external hard drive
-be able to access the drive with the ethernet input
-be able to access the drive as if it were an FTP server 

Thanks in advance ! :)

The RAID part have already been explained. However, if you have a spare drive, you might want to use it for system drive and keep the RAID array for data seperate. In that case, just do a normal install on the smaller drive and well help you setup the RAID array later.

For filesharing you want to setup Samba and a FTP server like PureFTPD, both are included in the Ubuntu repositories. There needs to be some configuration once the RAID is active.

I'm not sure if you can access your filesystem via USB from another machine as a normal drive. You would need special USB drivers that allows the host to switch to slave mode, and you would have to use NTFS on the RAID, which is way down the ladder of excellent filesystem choices for a setup like yours. You're better off with Samba over network.

---

