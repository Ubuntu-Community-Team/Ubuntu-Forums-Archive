---
title: "First Time Installing ----How to Partition"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by dw3bb10 on 2009-01-09
So, Ive always wanted to try linux but never came around to finding the right version for me. A friend of mine recently showed me his laptop running Ubuntu. I fell in love with it....And im now trying to install it on my laptop to mess around with. 

So, I downloaded the 64bit 8.10 version and burned the image to a cd. When setting up the OS for installation, ive encountered a problem when trying to partition my hard drive for installation. I want to install ubuntu on its own partition so that I can dual boot it, and Vista. I currently have a 160gb hdd, with only one partition for vista. Im trying to make another one, with around 10 or 12gb or so, soley for Ubuntu. The disk tries to get me to override the vista partition and use ALL the space on the hdd, OR use the remaining space. Which I dont want to do. Please assist me in this matter. Thanks,




---David

---

### Post by TSellers on 2009-01-09
One of the better tutorials I've seen:

Partitioning Windows and Ubuntu:
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by SteveHillier on 2009-01-09
From memory, and it is now some time since I did an install, (and I have not installed Intrepid), there is an option when you partition using only part of the disk to say which starting sector to use.  So, if for example, your disk has 10,000 sectors then you should be able to set the ubuntu partition to start at sector 5001 and it will take over and give you two equal amounts of space for Vista and Ubuntu.
Have a look and see but don't shoot me if I am wrong.  I no longer have dual boot machines so it is sometime since I looked at this.
Also make sure Vista is defragmented before you start.  Vista defragments itself normally but you have to be aware of odd system files hanging around in higher level sectors.
I have in the past asked ubuntu to shrink the Windows partition without prior defragmenting and it seemed to move the Windows data back into the Windows partition but don't rely on it.
It is also imperative to back up any vital Vista data just in case.  Burn your important files to CD.  You could possibly use the Easy Transfer Wizard (Start->All Programs->Accessories->System Tools->Easy Transfer Wizard) and drop this to a CD or USB stick, or use the Backup and Restore program to do the same.
Good luck

---

