---
title: "[SOLVED] Crossing the Divide"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by durant0s on 2007-11-24
I'm a newb trying to switch from XP to Ubuntu, and having problems reformating my hard drive.  Where should I begin?  I have a Ubuntu install cd, I have backed everything up, and I have installed ubuntu but still have xp installed.. any help here?

---

### Post by jcsteele on 2007-11-24
You want to completely remove your Windows XP partition/installation?  Or are you dual booting?  Please describe in detail what you want/plan to accomplish.

//jcs

---

### Post by durant0s on 2007-11-24
Yeah, I'm looking to not dual boot.  I looking to completely remove XP partition.

---

### Post by r00tintheb0x on 2007-11-24
When you go through the Ubuntu install process, select the option to "use entire drive". That'll nuke XP ;)

r00t

---

### Post by jcsteele on 2007-11-24
Since you have already installed ubuntu, you will not be able to simple remove your windows xp partition and "add" it to your ubuntu partition....your going to end up with two ubuntu partitions (depends on how you setup ubuntu in the first place).

The easiest suggestion to you is to reinstall ubuntu, and when it asks you how you want to install ubuntu, tell it to "use entire disk" under the guided partition segment of the install.  This will allow you to create on big partition for ubuntu and will use all ofyour hard disk (instead of splitting it up into two segments)...

If you do not want to reinstall, you can use gparted to delete the windows xp partition, etc.  However, I don't recommend it, but if you want just reply back and I will see what instructions I can come up with.

//jcs

---

### Post by durant0s on 2007-11-24
Cool thanks, it looks like that worked.  When I try and check my hard drive it says total capacity is 70, I have an 80, where did the other 10 go?  Does ubuntu partiton itself?

---

### Post by jcsteele on 2007-11-25
Ubuntu partitions a "swap" partition ([http://en.wikipedia.org/wiki/Swap_space](http://en.wikipedia.org/wiki/Swap_space)) automatically, which accounts for some of the space...

Even though your drive is specified as 80 gigabytes, in reality you will never be able to utilize all 80 gigabytes due to how operating systems allocate space (it does not matter what operating system) and how hard drive manufactures specify the capacity of their drives ([http://en.wikipedia.org/wiki/Hard_disk_drive#Capacity_measurements](http://en.wikipedia.org/wiki/Hard_disk_drive#Capacity_measurements))

Glad things are working.

//jcs

---

### Post by gali98 on 2007-11-25
If you feel this is solved you can mark it as so in thread tools.
Kory

---

### Post by durant0s on 2007-11-25
> **jcsteele said:**
> Ubuntu partitions a "swap" partition ([http://en.wikipedia.org/wiki/Swap_space](http://en.wikipedia.org/wiki/Swap_space)) automatically, which accounts for some of the space...

Even though your drive is specified as 80 gigabytes, in reality you will never be able to utilize all 80 gigabytes due to how operating systems allocate space (it does not matter what operating system) and how hard drive manufactures specify the capacity of their drives ([http://en.wikipedia.org/wiki/Hard_disk_drive#Capacity_measurements](http://en.wikipedia.org/wiki/Hard_disk_drive#Capacity_measurements))

Glad things are working.

//jcs

> **gali98 said:**
> If you feel this is solved you can mark it as so in thread tools.
Kory

Thanks I appreciate it.

---

