---
title: "Says I only have 981Mb free on hard drive?"
date: 2009-09-19
forum: Hardware
---

### Post by WatTwo on 2009-09-19
When I am on Ubuntu, look at "filesystem" it says i only have 981Mb free. but when i look at the partition in windows i have 9Gb free.

Anyone know why this is?

Thanks!

---

### Post by cholericfun on 2009-09-19
simple:

how do you look at the ext part from windows?
your windows part. has the 9G,
your ubuntu part hasnt.

---

### Post by 73ckn797 on 2009-09-19
> **WatTwo said:**
> When I am on Ubuntu, look at "filesystem" it says i only have 981Mb free. but when i look at the partition in windows i have 9Gb free.

Anyone know why this is?

Thanks!

See if this will help: [http://ubuntuforums.org/showthread.php?t=1270467](http://ubuntuforums.org/showthread.php?t=1270467)

---

### Post by drs305 on 2009-09-19
Here's another post to check out. The most common reasons for disappearing disk space include undeleted root trash, large log files, and backups saved to the wrong location (because the backup partition wasn't mounted).

This guide gives you ways to identify and correct these and other issues:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by gordintoronto on 2009-09-19
> **WatTwo said:**
> When I am on Ubuntu, look at "filesystem" it says i only have 981Mb free. but when i look at the partition in windows i have 9Gb free.

Anyone know why this is?

Thanks!

Is this a Wubi install?

---

### Post by WatTwo on 2009-09-19
Well i think i know why now, when i installed ubuntu, it said "amount of disk space for install" (or something like that) i selected 4 gigs, ( i figured it was the amount of space for the OS files)

So i need to make this larger, but how do i do it?

thanks!

And yes, Wubi install

---

### Post by drs305 on 2009-09-19
Wubi installs are not really meant to be resized. Nevertheless, there are some things you can do, such as creating a virtual disk. Take a look at this section of the Wubi wiki for some possibilities:
[https://wiki.ubuntu.com/WubiGuide#How big should the the virtual disks be?]("https://wiki.ubuntu.com/WubiGuide#How big should the the virtual disks be?")

---

### Post by WatTwo on 2009-09-19
Okay well, i might delete my whole ubuntu then, but how can i install it in just one partiton?

That's what i tried in the first place, but it wanted to mess around with my windows partition : /

---

### Post by 73ckn797 on 2009-09-20
> **WatTwo said:**
> Okay well, i might delete my whole ubuntu then, but how can i install it in just one partiton?

That's what i tried in the first place, but it wanted to mess around with my windows partition : /


You can resize the Windows partition from the LiveCD using Gparted. Once resized you can setup the second partition and then install Ubuntu. You may have to perform a "chkdsk" for the Windows partition after resizing. That would have to be done from Windows or using the Windows disk.

I would first uninstall the Wubi install.

---

### Post by oboedad55 on 2009-09-20
> **73ckn797 said:**
> You can resize the Windows partition from the LiveCD using Gparted. Once resized you can setup the second partition and then install Ubuntu. You may have to perform a "chkdsk" for the Windows partition after resizing. That would have to be done from Windows or using the Windows disk.

I would first uninstall the Wubi install.

And then defrag your drive thoroughly. I bricked a windows installation by not defragging first.

---

### Post by drs305 on 2009-09-20
If you decide to reinstall and choose "side by side" with Windows be careful in Step 4. You must click on the partitioning bar at the bottom of the page and increase the partition size. If you don't, a default partition size of 2.5GB will be used, which is too small. 

It's a known bug in the installer and is being worked on. Here is a link that explains it a bit further, including a graphic:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

---

### Post by 73ckn797 on 2009-09-20
> **oboedad55 said:**
> And then defrag your drive thoroughly. I bricked a windows installation by not defragging first.

This too.

---

