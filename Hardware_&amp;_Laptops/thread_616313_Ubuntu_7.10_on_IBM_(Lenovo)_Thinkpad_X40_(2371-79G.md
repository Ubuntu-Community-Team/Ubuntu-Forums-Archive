---
title: "Ubuntu 7.10 on IBM (Lenovo) Thinkpad X40 (2371-79G)"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by stralien on 2007-11-18
Dear friends,

This is my first post in Ubuntu Forums. (Forgive my English, I will try...) :)

I have installed the Ubuntu 7.10 on an IBM (Lenovo) Thinkpad X40 (2371-79G) with a 1.8" 8GB Transcend Solid State Disk in the place of the factory 40GB HDD.
Everything work fine. Ubuntu had recognize everything including my wireless network (Apple) and the docking station and everything else as net printers e.c.c. And it can communicate with any shared hdd (like WD world) or computer. (Apple iMac Intel everything osx.)
And it works so unbelievably fast!
But I had the following question: Ubuntu is installed with everything that it had automatically  chosen. And that includes the file system. And as you know the ssd's feel more comfortable with file systems that are aware with the "read/write/time last" fact. As I saw the Ubuntu is installed with the ext2 file system and as I read in the KernelTrap site ([http://kerneltrap.org/node/8159](http://kerneltrap.org/node/8159)) there is the jffs2 file system (very similar to ext2 as they said).
So, this is my question: Do I have to install another file system;

Thanks in advance for your time and I am ready to supply you with any other detail you'd like about my installation.

George Glikofridis
Athens
Greece.

---

### Post by regomodo on 2007-11-18
Ubuntu is actually installed with ext2 by default which is more or less the same as ext2 but journaled.

About your question, i have no idea. Sorry

---

### Post by frank.wagner on 2007-11-20
Hi stralien, Hi other X40 and Ubuntu User,

yesterday, i purchased an X40 (used - ebay)

First, I wanted buy an Asus eee 4G - but the decision went in the direction Thinkpad X40
[LIST]
[*]Because I want to use Ubuntu 7.1 and an 8GB 1,8" (or16GB) Transcend Flash Card
[/LIST]
**My questions:**

1) Where can I buy a good SSD Flash an it runs with Ubuntu  (to replace the factory 40GB HDD) ???
[LIST]
[*]Transcend TS8GIFD18 1.8" 8GB IDE Internal Solid state disk - 180 $
[/LIST]
[IMG]http://images10.newegg.com/NeweggImage/productimage/20-208-063-03.jpg[/IMG]

2) Is the reconstruction complex ???

Thanks for your Feedback

Frank
[COLOR="Blue"]
Hi stralien - Did you have pictures of the reconstruction[/COLOR]

---

### Post by stralien on 2007-12-27
It is not a good thing to reply one month later... I am really sorry...
Anyway...

No, the reconstruction it is not complex, just follow the hard disk replacement manual from the IBM support site.
Disable from the BIOS the system possibility to access the special IBM HDD recover partition.
I used the extra cdrom that came with the docking cradle. Because this is the way to boot from this cd to install Ubuntu.
I had exactly the same ssd, and everything works fine but I had notice some boot problems for time to time. Very rare I had to say but this is probably a motherboard problem. Maybe the motherboard can not give the right current to the ssd.

I bayed the ssd from the German Transcend site because of the EU.

Hope I help and i am really sorry for the delayed reply again.

STRalien

---

