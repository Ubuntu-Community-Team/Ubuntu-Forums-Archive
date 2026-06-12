---
title: "Broken RAID on install"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by Weewolf on 2009-01-14
This is the first time I have ever tried Linux/Ubuntu so please bear with me.

Setup:
[LIST]
[*](Trying to setup) dual boot Windows/Ubuntu onto a RAID0
[*][Using the built in raid function of this motherboard. (link)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131284")
[*]2 Hard drive raid split into two partitions: OSDrive, and MediaDrive.
[*]I'm trying to install off of the live CD.
[/LIST]


[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Following the long instructions in method 2 I get the follow errors on step six:

ubuntu@ubuntu:~$ sudo dmraid -ay
ERROR: isw device for volume "OSDrive" broken on /dev/sda in RAID set "isw_dbccbdgbff_OSDrive"
ERROR: isw: wrong # of devices in RAID set "isw_dbccbdgbff_OSDrive" [4/2] on /dev/sda
ERROR: isw device for volume "MediaDrive" broken on /dev/sda in RAID set "isw_dbccbdgbff_OSDrive"
ERROR: isw: wrong # of devices in RAID set "isw_dbccbdgbff_OSDrive" [4/2] on /dev/sda
ERROR: isw device for volume "OSDrive" broken on /dev/sdb in RAID set "isw_dbccbdgbff_OSDrive"
ERROR: isw: wrong # of devices in RAID set "isw_dbccbdgbff_OSDrive" [4/2] on /dev/sdb
ERROR: isw device for volume "MediaDrive" broken on /dev/sdb in RAID set "isw_dbccbdgbff_OSDrive"
ERROR: isw: wrong # of devices in RAID set "isw_dbccbdgbff_OSDrive" [4/2] on /dev/sdb

I have done some searching around and I have not been able to find an explanation on what this error is or how to fix it that I can understand.  Any help would be much appreciated.  

-Wee

---

### Post by Weewolf on 2009-01-20
No thoughts on this one?

---

### Post by Clawson on 2009-01-23
I am also interested in this post, i have been searching around for raid 0 dual boots and i saw this post and it matches what i want to accomplish.

Good luck!  Hopefully the smart Ubuntu people bail you out!

Matt

---

### Post by Weewolf on 2009-01-26
Still no luck!  One more bump before I give up.  :(

---

### Post by mspisars on 2009-01-27
according to this [http://www.honeytechblog.com/intel-matrix-storage-manager/](http://www.honeytechblog.com/intel-matrix-storage-manager/)
your raid is only supported on windows OSes
click the download link at the bottom and you will be taken to the intel download page. Where it asks you for your operating system...
You can have either a linux or windows but I do not think you will be able to have it dual boot. I think the same software would have to exist for both operating systems.

Cheers.

---

### Post by mspisars on 2009-01-27
Well, then there is this: [http://www.driverheaven.net/linux-operating-systems/119256-linux-support-intel-ich7r-raid.html](http://www.driverheaven.net/linux-operating-systems/119256-linux-support-intel-ich7r-raid.html)
Although the above mother board has the ICH9R chipset...

---

