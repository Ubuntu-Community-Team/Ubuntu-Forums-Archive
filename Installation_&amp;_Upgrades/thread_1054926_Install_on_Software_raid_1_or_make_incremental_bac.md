---
title: "Install on Software raid 1 or make incremental backups?"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Fredrik_b on 2009-01-30
I´m getting 2 new hard rives for my system (OS) (My old hard drives will not play nice annymore)

I have 3 possible installation scenarios 

1) Software Raid 1
This article suggest might not be the best solution. - [https://help.ubuntu.com/community/Installation/RAID1](https://help.ubuntu.com/community/Installation/RAID1)

2) Software raid with System partition on an USB stick (and clone this to a backup USB stick). One downside if this is that I have to buy two new US sticks. Allot cheaper the the best solution, to buy a real raid card. But still a cost. This however does not seem to be a good solution sins he system will basically run rum the USB stick, and also some downtime.

3) Make a incremental backup/clone of the system drive every day. (will need an how to for this)
This alternative would of course mean some downtime until I remove the broken hard drive if it fails. 
This is ok, I just don't want to have to reinstall and setup all apps again.


What will happened on 1) if one of the drives fails? will the system still boot? Why is it a bad idea to put the system partition on an software raid 1 array?

---

### Post by callan79 on 2009-01-30
> **Fredrik_b said:**
> I´m getting 2 new hard rives for my system (OS) (My old hard drives will not play nice annymore).
What will happened on 1) if one of the drives fails? will the system still boot? Why is it a bad idea to put the system partition on an software raid 1 array?


Hi Fredrik_b,

I can't comment on RAID - I know what it is, but I've never used it.

I'll tell you my solution though. This solution works for me, and for a number of other people who I have set up the same way.

1. My computer has two hard drives. Firstly, a small 120GB for Ubuntu system files. Then, a 400GB IDE for backup purposes.

2. I have a network storage device - one of [THESE](http://www.repotec.com.tw/default.asp?pagename=Network_Storage/RP_NA2310.htm) and it's absolutely awesome. I store ALL my data on this device (except mail, bookmarks etc).

3. I use the Ubuntu 'SimpleBackups' software which you can install from Add/Remove Programs. It puts an icon on your System >> Administration area. It backs up data from my network storage, to the second hard disk in my machine. It does this daily, incremental. Then it does a full backup every 21 days.

4. I don't do this, but I should - if you want absolute redundancy, you should store the network storage device in a different room to your computer. So this protects against fire/damage/theft.


Also, you don't need the network storage device. You could just aswell do the same process between two hard disks within your computer...

Hope this helps :)

Cheers
Callan

---

### Post by Fredrik_b on 2009-01-30
My main storage is in the same computer. I have 4 750GB hard drives that I have in Raid 5 using mdadam. But these drives is farly independent from the system. If i have to reinstall the system compleatly it only takes 2 min to reasemble the raid 5 array.

The important thing for me is to get the system and all settings for torrents webserver and other apps up and running with the least amount of work if the system drive fails.

Reinstalling ubuntu only takes 12-15 minutes, but it is restoring all programs and settings that takes a long time if the system failes. 

I will test SimpleBackups and se if it meets my needs

---

