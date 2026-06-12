---
title: "Laptop overheating on Ubuntu but not on Vista"
date: 2010-10-31
forum: Hardware
---

### Post by djhorry on 2010-10-31
Hello everyone! I have a Fujitsu Siemens (Amilo) laptop: 2GbRAM, 1,70Ghz & 256MbVideo. It came with Vista Ultimate, I've been using that for a year now, and this week I have installed Ubuntu. I have 3 partitions: C:\(with Vista); D:\ (data) and L:\ (Ubuntu). When I start up my laptop, I can select which OS to use. If I use Vista, my laptop does get warm in like 1-2 hours. But if I use Ubuntu, it gets really hot in 30mins, and the fan keeps working hard non-stop.  On Vista, the fan runs like 10secs, then it stops, and 10secs again in a few minutes. 
Please help me! *Thank you*! :P

+is it ok if I install Ubuntu on a 3rd partition on ASUS m51vr? 

P.S. Sorry for my grammar mistakes, I'm not a native speaker!

---

### Post by P4man on 2010-10-31
Is CPU scaling working? Right click the panel, add to panel, select CPU frequency scaling monitor. If that gives no error, make sure you set it to ondemand or powersave.

---

### Post by P4man on 2010-10-31
BTW, those partitions are windows partitions. The only way to install ubuntu there is using wubi, and I wholeheartedly recommend you avoid wubi, especially since you dont mind partitioning. The only point of wubi is being able to install inside the same windows partition. 

Instead I would suggest you boot ubuntu from CD or USB to install on to its own partition.  Then you have a native install.

---

### Post by Jimtheplanner on 2010-10-31
Hi Folks,

This is a similar post to [http://ubuntuforums.org/showthread.php?t=1600307](http://ubuntuforums.org/showthread.php?t=1600307)

I did a back to back clean install between 10.10 and Mandriva 2010.1 just to prove my hardware. I found that Mandriva was a cool 40 deg C where 10.10 was cooking my hardware at good 10+ Degs C higher.

I can speak for Windows never used in almost 10 now....wow freedom

Jim

---

### Post by djhorry on 2010-11-06
Thank you! :)

---

