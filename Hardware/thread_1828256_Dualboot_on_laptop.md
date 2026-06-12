---
title: "Dualboot on laptop"
date: 2011-08-18
forum: Hardware
---

### Post by parth.s on 2011-08-18
I just bought a new an Acer Laptop and I want to dual boot it with Ubuntu 10.04 and Win7. I have been using a dual boot desktop at home.
Before i begin i have a few queries :
 - Will this void my laptop warranty?
 - Just after i bought my laptop i created a 'Factory Default Disc' through the acer eManagement software (took me 3DVD's). Will this suffice, if i want to preserve my genuine Win7 that was pre installed with the laptop and if plan to bring my system to its default state.

Apart from this i have also taken a backup of the drivers, a windows Sytem image and a windows repair disc.

Cheers

---

### Post by dave01945 on 2011-08-18
as far as i'm aware software doesn't void warranty best check warranty details to be 100% and the recovery disks you burnt should return the laptop to factory condition (this was the case with my hp laptop) it's basically away of reinstalling windows **when** it goes wrong

---

### Post by parth.s on 2011-08-18
So I think its safe for me to start with installing ubuntu, right?

---

### Post by dave01945 on 2011-08-19
yeah it's safe even if you remove windows the recovery disks will reinstall it

---

### Post by corncob on 2011-08-19
I'm getting a bit off-topic here but I had some trouble installing Ubuntu on my Asus eeebox.  Win7, they tell me, only needs two partitions, but the OEM had added 2 more thus filling up the drive with the maximum of 4 primary partitions.  Acer might not do that and you're installation will go smoothly but post back or start another thread if you run into problems.

---

### Post by Basher101 on 2011-08-19
he said eManagement so i guess you have an eMachines laptop (like me). It has hidden recovery partitions so i guess he has 4 primary partitions already. I also noticed GParted does not even let me create an extended partition when 4 primary are already there. Though an extended can contain more than 4 primary partitions..i dont get why it wont let me create the extended

---

### Post by oldfred on 2011-08-19
The extended partition which can hold many logical partitions is one of the primary partitions. So you can have 4 primary partitions or 3 primary and one extended (which is still a primary).

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

While discussing HP primarily, it applies to all windows with 4 primary partitions used, which most vendors with win7 seem to do. 

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by corncob on 2011-08-20
> **Basher101 said:**
> he said eManagement so i guess you have an eMachines laptop (like me). It has hidden recovery partitions so i guess he has 4 primary partitions already. I also noticed GParted does not even let me create an extended partition when 4 primary are already there. Though an extended can contain more than 4 primary partitions..i dont get why it wont let me create the extended

I was going to say that the largest partition on my eeebox was empty and marked as "storage".  I deleted it and created a logical (extended) partition in the resulting unallocated space and installed Ubuntu there.  Win7 appears unaffected but then I don't use it much either.  Oldfred seems to have everything covered.

---

### Post by parth.s on 2011-08-27
Thanks! :guitar:

---

