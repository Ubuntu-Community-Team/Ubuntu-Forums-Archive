---
title: "Help Installing New Drive In Ubuntu Server 8.04"
date: 2008-09-16
forum: General Help
---

### Post by FarehamWeather on 2008-09-16
I am new to ubuntu and I am trying to install a new drive.

I need help creating partitions on the drive and formating them.
Please can you give me the commands :)

Thanks alot!

---

### Post by Elfy on 2008-09-16
You will need to use fdisk to create the partitions - you will need the logical name for the drive eg sda.

Once the partitions have been made you need to create filesystems on each partition with mke2fs. Folders need to be created for the mountpoint with mkdir in order for them to mount.

There is a help page detailing the process - [https://help.ubuntu.com/community/InstallingANewHardDrive#Command](https://help.ubuntu.com/community/InstallingANewHardDrive#Command) Line Partitioning

HAve a read and come back with your questions

---

### Post by FarehamWeather on 2008-09-16
That worked thanks!

What is the first and last cylinder?
how can I make it use the entire disk?

---

### Post by Elfy on 2008-09-16
Not sure for you - but ```
sudofdisk -l
```should givwe you the information you need.

---

### Post by FarehamWeather on 2008-09-16
Thanks alot! :)

---

