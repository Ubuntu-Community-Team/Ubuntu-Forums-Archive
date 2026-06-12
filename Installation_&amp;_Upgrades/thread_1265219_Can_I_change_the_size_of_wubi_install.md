---
title: "Can I change the size of wubi install?"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by Norman IV on 2009-09-13
Hello! I am basically a newb to Linux and Ubuntu. I initially installed Ubuntu on my computer because I was taking a Linux class online. Once I figured out how to get all my multimedia working properly and learned a bit about the Ubuntu philosophy I came to realize how awesome it is and now use Ubuntu as my primary operating system. At first I tried having the installation make a new partition on my second HDD, but after repeated attempts with an error each time I instead installed Ubuntu from Windows XP. I chose the 4GB option because thought I only wanted enough space for the filesystem and some misc files. Now that Ubuntu is my primary OS I am wondering if there is any way to increase the amount of space allocated by wubi. I know the ideal thing would be to make its own partition, but I would really prefer not to have to move the installation right now...

---

### Post by Partyboi2 on 2009-09-13
Hi you should be able to use [[COLOR=Blue]LVPM[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?") to resize your virtual disk.

---

### Post by Norman IV on 2009-10-27
Sorry I didn't reply sooner, my concern abruptly became a much bigger problem and I have had so little free time lately. I knew I was low on disk space, but I didn't know just HOW low. I had been ignoring the automatic update reminder for some time and I finally decided to let it go ahead. There were a number of updates and I completely ran out disk space during a kernel update. After this, Ubuntu would not boot successfully (got an error saying something about 175 and panic not found). I was able to boot into recovery mode but most of the GUI programs wouldn't even load and I assumed I would have no room to install LVPM. The LVPM website did have a mini linux based partition manager that I could boot into, so I renamed root.disk and re-did the wubi install with a 10gb vdisk. When I booted to the mini partition manger OS I mounted the old virtual disk and copied all the files to the new one, overwriting the fresh install. I was able to boot at this point but the owner/permissions were all screwed up and the system did not function practically.

   I am a complete newb to Linux, and although I know my way around a computer I don't have all the skills of a true computer nerd. I became fed up and simply re-did the wubi install (again), downloaded updates, and I am copying personal data and other settings from the old virtual disk as needed ( basically just the stuff from my home folder including the "." hidden directories for firefox and evolution etc).

Anyway, sorry to rant; I probably sound like an ignorant newb, but then again I am one so...  Anyway everything is tip top now. If anyone reads this and knows of a better way I could have fixed my problem please post it. I have fixed the problem but I would appreciate the learning experience.

---

