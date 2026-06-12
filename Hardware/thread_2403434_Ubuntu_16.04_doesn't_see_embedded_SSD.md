---
title: "Ubuntu 16.04 doesn't see embedded SSD"
date: 2018-10-11
forum: Hardware
---

### Post by alextimeoff on 2018-10-11
Hi, everyone!
I have the new laptop Dell Inspirion 15 7000. Windows 10 was preinstalled on it. This laptop has a HDD 1Tb and I enter a SSD 500GB into one. I want to install Ubuntu 16.04 on the second disk but Ubuntu doesn't see it. Windows and BIOS see the second disk. sudo fdisk -l out the same. Help me, please. Thank you!

---

### Post by oldfred on 2018-10-11
Dell need UEFI update & SSD needs firmware update.

And Dell sets drives to RAID, you need to add AHCI drivers into Windows and change settings for drives to AHCI.

Then you must be sure Windows fast start up is off. That is hibernation and prevents the Linux NTFS driver from correctly seeing the partitions.
Note that Windows with updates will turn fast start up back on.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

