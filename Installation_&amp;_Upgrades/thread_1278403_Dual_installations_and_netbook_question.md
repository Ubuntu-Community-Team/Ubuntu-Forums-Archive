---
title: "Dual installations and netbook question"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by daveycakes on 2009-09-29
Hi there, :) glad to apart of the forum. Been using Ubuntu for over a year now (still learning the basics) and i thought it was time to register on here. So hello :)
 
Anyway couple of questions straight off.
 
When I created a seperate partition on my hdd for ubuntu the grub loader removed the windows boot file. I was wondering how I could avoid this?
 
Secondly, just bought a netbook (Dell inspiron mini 10v) for lectures. It comes with Ubuntu 8.04; now I've noticed the there is a new desktop edition advertised on the main page. Would it be advisable to install that onto my new netbook?
 
Many thanks, and hello once again :)
 
daveycakes

---

### Post by raymondh on 2009-09-30
> **daveycakes said:**
> Hi there, :) glad to apart of the forum. Been using Ubuntu for over a year now (still learning the basics) and i thought it was time to register on here. So hello :)
 
Anyway couple of questions straight off.
 
When I created a seperate partition on my hdd for ubuntu the grub loader removed the windows boot file. I was wondering how I could avoid this?
 
Secondly, just bought a netbook (Dell inspiron mini 10v) for lectures. It comes with Ubuntu 8.04; now I've noticed the there is a new desktop edition advertised on the main page. Would it be advisable to install that onto my new netbook?
 
Many thanks, and hello once again :)
 
daveycakes


Hello and welcome .

There needs to be a bootloader to access the OS.  On a system with 2 HD's ..... you can choose to install GRUB in the MBR (master boot record) of the second HD hence preserving the existing bootloader (and MBR) in the 1st HD.  Now if your system only has 1 HD, you have to choose and install which bootloader to use.  Unfortunately, I don't know if windows' can access a linux install.  Linux, however, has bootloaders (GRUB, LiLO, etc.) that can access a windows install.  I prefer to simplicity and flexibility of GRUB.

Regarding your Dell mini 10, I read somewhere in the forum that there are limitations about using/upgrading to a different version on a pre-installed DELL system.  I believe the 8.04 you have currently is "special" to the mini 10.   You may want to post this question in the dell sub-forum here in ubuntuforums.  Nevertheless, I would try a live session first (need to make a liveUSB) to see how the new version plays/reacts to your system specs'.  On a side note, I like the long-term support of 8.04.

Hope I was clear.  If not, am sorry and will try to be more concise in my next post.  I need my morning coffee :)

Regards,

---

### Post by robbieo11 on 2009-09-30
I have a msi wind simalar to dell mini.
It came with the xp install so i installed ubuntu also  i have tried the netbook edition  it was ok  i realy like the desktop version better just works better for me. Anyway to answer  yes ubuntu desktop will work it is the same os  

In fact if you want you can go to synapics package manager  search netbook remix anything that is green is installed  right mouse and deinstall

---

