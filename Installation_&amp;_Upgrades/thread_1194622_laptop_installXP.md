---
title: "laptop install/XP"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by skyeking on 2009-06-22
I have a Dell 9100 notebook running XP Pro and would like some advice on installing Ubuntu while removing XP. My attempts to format the harddrive indicate this must be done from outside either from another partition or another drive. I'm also thinking I might be able to get the job done by directly networking (ad-hoc) another notebook and format from the second PC.
Any good advice/previous experience will be greatly appreciated.
-skyeking- :confused:

---

### Post by lindsay7 on 2009-06-22
If you no longer want xp on you computer the Ubuntu installation will give you and option to use the whole disk drive for the Ubuntu installation.  Doing so will get rid of Windows if that is what you want.

---

### Post by presence1960 on 2009-06-22
+1

short and sweet...they are the best answers, although a lot of times things aren't quite that simple!

---

### Post by skyeking on 2009-06-24
Thanks Lindsey....that's what I needed!

---

### Post by presence1960 on 2009-06-24
skyeking, for future reference did you know that you can use the Ubuntu live cd to partition any machine regardless of what is installed on it? Boot the CD and choose "Try Ubuntu without any changes". When the desktop loads open a terminal and run ```
gksu gparted
``` or go System > Administration > Partition Editor. You will be able to format and/or partition all disks because none of them will be mounted. You can also download the gparted Live CD and use that.

---

