---
title: "RocketRAID 3000 Series: Native Support Ubuntu 8.04"
date: 2008-07-08
forum: Hardware
---

### Post by soundengine355 on 2008-07-08
Hi All,

I've been searching for a good RAID Controller that is natively supported by Ubuntu 8.04. After some checking apparently the RocketRAID 3000 Series supports Ubuntu.

[http://www.highpoint-tech.com/USA/series_3000.htm](http://www.highpoint-tech.com/USA/series_3000.htm)

Native Linux Support for the Following Linux Distribution:

RocketRAID 3510/3522/3540 Embedded into kernel 2.6.25 and up
From 8.10 and higher

RocketRAID 3520 Embedded into kernel 2.6.24 and up
From 8.04 and higher	

RocketRAID 3220 and 3320 Embedded into kernel 2.6.18 and up
From 7.04 and higher

RocketRAID 3120 Embedded into kernel 2.6.25 and up 
From 8.10 and higher 	

Is anyone using the 3000 Series? Can you confirm this?

---

### Post by rbm0307 on 2008-08-14
Bump....

I have also been searching for an Ubuntu-based RAID solution and am looking at the RocketRAID 3510.

Does anyone know if 8.04 LTS will include the native support code for the 3510 come October?

---

### Post by ubumac on 2008-09-02
I am also looking for HW-based RAID card supported on 8.04. Any further update on compatibility of the rocketraid card?

---

### Post by shiler00 on 2009-10-13
I can't believe noboby has posted a relpy to any one in this thread in a year now. Do rocketraid products not work in 8.04.2. I says it has native drivers but every time i get to the partition page it is empty. I'm assuming that means that it cant load the rocketraid 3120 driver. I'm new to ubuntu but am getting discuraged by the time i have spent looking for help getting this 3120 to be recognized.

---

### Post by johnzollo on 2009-10-19
I'm sorry.  I have an older RocketRAID card that worked fine in Windows, but does not have modern Linux support (dmraid does not work for it).  I've heard mixed reviews on NewEgg.com about the Highpoint controllers and Linux.  Good luck getting it to work!

Sincerely,
John

---

### Post by AllGamer on 2011-04-25
just shedding some light into this topic.

most people have probably already moved on to a newer version of ubuntu, or another RAID controller altogether, but in the odd some of you are still looking for the answer, coming from Google

the drivers can be compiled manually in the latest ubuntu 10.x and 11.x with simply running 

```
sudo make install
```

you might get some error, but they are usually safe to ignore, example:
[http://ubuntuforums.org/showthread.php?t=1612915&highlight=rr1740](http://ubuntuforums.org/showthread.php?t=1612915&highlight=rr1740)

and the RAID controller software are also working on 10.x & 11.x beta
details:
[http://ubuntuforums.org/showthread.php?t=1737847](http://ubuntuforums.org/showthread.php?t=1737847)

---

