---
title: "System restore?"
date: 2008-09-14
forum: General Help
---

### Post by ManyBeers on 2008-09-14
I just installed Ubuntu 8.04 on My Sony laptop WindowsXP SP3 machine. I always have 
System Restore enabled on My C:\drive(Windows) and disable it on my D:\drive(apps
storage). Since installing Ubuntu I installed this software:
[http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html")
(Allows read/write on ext2/3 volumes from within Windows)
which shows both my Ubuntu , and  Swap Partition. Now in System Restore the swap 
partition does not show up but the Ubuntu partition does and it is being monitored. I click the drive select disable system restore on this drive but I cannot disable it. I get this error message :
"System restore encountered an error enabling/disabling system restore on one or more drives.
Please restart your computer and try again."  There is no System Volume Information which 
stores restore points though. So is this something to be concerned about?

---

### Post by cariboo on 2008-09-14
System Restore is the first thing I diable, as it is a great place for malware and viruses to hide. There is no equivalent to system restore in Ubuntu, but there a lot of backup utilities to help you make a complete backup of your system. Open up System-->Administration-->Synaptic Package Manager and search for backup and you will get a listing of all the backup programs available. I use simple backup which does a full backup at the start of the week then incremental backups afterward. Simple backup can be setup to do that backup automagically so you never have to think about it.

Jim

---

### Post by ManyBeers on 2008-09-14
> **cariboo907 said:**
> System Restore is the first thing I diable, as it is a great place for malware and viruses to hide. There is no equivalent to system restore in Ubuntu, but there a lot of backup utilities to help you make a complete backup of your system. Open up System-->Administration-->Synaptic Package Manager and search for backup and you will get a listing of all the backup programs available. I use simple backup which does a full backup at the start of the week then incremental backups afterward. Simple backup can be setup to do that backup automagically so you never have to think about it.

Jim
I have used Systen Restore in the past and it works flawlessly, of course I have never gone back more than 2 days and therefore I only keep enough diskspace enabled for 4-5 restore points.
Secondly I am trying to disable it on Ubuntu's drive. I don't want Windows monitoring it. 
Though i don't know if it actually is because as i stated "There is no System Volume Information
folder though".

---

