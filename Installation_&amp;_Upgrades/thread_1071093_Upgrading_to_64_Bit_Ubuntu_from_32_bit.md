---
title: "Upgrading to 64 Bit Ubuntu from 32 bit"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by Neko_Master on 2009-02-15
Ok I dont have more then 4GB of RAM but I know that my CPU (AMD Atholon 64 x2 5000+) is a 64bit Dual COre. The thing is some of my games (openttd inparticular) is having problems using many mods running my 32 Bit Ubuntu

Now I relise Ill prob need to do a clean install but is there anyway install a 64 bit Ubuntu over my existing 32 bit ubuntu?

---

### Post by sirjoebob on 2009-02-15
It depends. If you just did a guided install and everything is on one partition, you'll probably have to format. I had a seperate "/" and "/home" partition, so i could install the entire OS and still have my home folder. also, you should definitely do it. I installed 64 bit yesterday and many things seem to have a certain snappiness to them, I will never go back to 32 bit. Many peiple say there is a lot of missing packages, etc but i havent found anything.

---

### Post by pansz on 2009-02-15
> **sirjoebob said:**
> It depends. If you just did a guided install and everything is on one partition, you'll probably have to format.

I see no reason to format the disk if you install on one partition. Ubuntu installer will delete everything except /home directory when installing to an existing ext3 partition, that basically is more convenient than a separate /home.

So a clean install is not neccesary since it is essentially equivalent to installing on a existing system. Simply remember to choose Manual partition and do *not* format the partition when install.

---

### Post by sirjoebob on 2009-02-15
Wow. I stand corrected. I did NOT know that. there's an option for you then!

---

