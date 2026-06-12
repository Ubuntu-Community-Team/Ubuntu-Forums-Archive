---
title: "Can't install Ubuntu 9.04"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by dawc159951 on 2009-08-07
Hi, i have been trying to install Ubuntu 9.04 inside Windows but is just copying the files to the hard drive and after the cd does that the install windows is just closed, nothing else happens, when I check the Ubuntu folder, it just has an ISO file and some folders, I'm using an original CD and also I tried with a CD image downloaded from the web. What should I do to install Ubuntu? or in case I can't install itvinside Windows, can someone tell me the way to install it in any other hard drive partition without formating it, because I can't really lose all my data.

Thanks a lot.

---

### Post by running_rabbit07 on 2009-08-07
Have you tried Wubi? If you put the disk in while booted into Windows, it should offer to install within Windows. It will install in the same manner as any other program you use. After installing when you boot up you will be given the option to boot Windows or Ubuntu. 

Otherwise you will need to resize your Windows partitions to make room for it. I can honestly say that I play with my partitions a lot and have yet to lose any data. If you do decide to resize your partition be sure to do at least one defrag first. Defragging moves all of your files to the front of the disk.

---

### Post by dawc159951 on 2009-08-07
> **running_rabbit07 said:**
> Have you tried Wubi? If you put the disk in while booted into Windows, it should offer to install within Windows. It will install in the same manner as any other program you use. After installing when you boot up you will be given the option to boot Windows or Ubuntu. 

Otherwise you will need to resize your Windows partitions to make room for it. I can honestly say that I play with my partitions a lot and have yet to lose any data. If you do decide to resize your partition be sure to do at least one defrag first. Defragging moves all of your files to the front of the disk.


When I start from the CD it doesn't give me any option to install within windows, but when I start windows and the put the CD it gives me the option, but the problem is that is not working :/ after copying some files it says "copying (or extracting, don't remember) Kernel" and that's it, nothing else happens. I think I will just backup all my data and install from my 2nd partition, that would be easier I think.

Thanks for your help.

---

### Post by merlinus on 2009-08-07
If you downloaded the 9.04 .iso, that is for installing into a separate partition on your hdd.  Boot from the cd, and follow the directions.  At the partitioning screen, choose side-by-side with windows.

wubi is a different download altogether that is run from and installed within windows.

---

### Post by TheSpartin on 2009-08-07
if you boot from the cd it should give you an option to select a hard drive and format the free space on it into a partition for ubuntu, or atleast mine did

---

### Post by dawc159951 on 2009-08-07
I'm already installing it in my laptop, I decided to use the free space of a partition, I was just confused because when I installed the old version I haven't this problem, I just installed within windows and using Wubi and worked very well, was a surprice that this version wasn't working fine, but anyway I think is better in this way, Windows will be deleted soon or later haha.

Thanks for all your help.

---

### Post by TheSpartin on 2009-08-07
> **merlinus said:**
> If you downloaded the 9.04 .iso, that is for installing into a separate partition on your hdd. Boot from the cd, and follow the directions. At the partitioning screen, choose side-by-side with windows.
 
wubi is a different download altogether that is run from and installed within windows.
 
Actually, when i downloaded 9.04's iso, it had wubi on it for if you wanted to install it while in windos, my AV just kept blocking it and picking it up as a threat

---

