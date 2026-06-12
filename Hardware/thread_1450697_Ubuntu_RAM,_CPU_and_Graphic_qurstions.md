---
title: "Ubuntu RAM, CPU and Graphic qurstions"
date: 2010-04-09
forum: Hardware
---

### Post by Ullyxes on 2010-04-09
Hello everybody!
I'm new (it's installed around 2 days) in Ubuntu (9.10-32bit) and I already have some really important questions. 
1---Before, i ran Windows XP Home Edition (SP 3) and in idle mode the RAM usage was around 180MB , CPU(s) usage 0-2%...........
now in Ubuntu in idle mode the RAM is used up around 220-340MB and the CPU(s) Usage is around 4-9%   (Sys specs: Intel Celeron E1400 2x2.00Ghz, 2GB DDR2 RAM, ASUS Nvidia Geforce 9400GT Silent, 250GB HDD (Ubuntu has a 55GB partition)
NOW to come to the question: is such a usage usual at Ubuntu (because Free), or can i get i down a bit by killing some unnecessary processes (if yes, which??)??????

2---My Graphics driver has this PowerMizer, but actually i don't need this, how can I turn it off, that my Graphic Card !!always!! has the better Shader etc. Frequencies?????

Thanks in forward to your answers   A totally Ubuntu NooB


P.S: Without these problems Ubuntu:guitar::guitar:!!!!

---

### Post by Paddy Landau on 2010-04-09
Welcome to Ubuntu!

These are three different questions. In future, it may be helpful to post three different threads, one for each.

I can answer your first question about RAM. Linux uses unused RAM for buffering. Thus, the RAM reading is not comparable to Windows. Your *minimum* RAM needs are less than those on Windows, but Linux uses extra simply because it's available.

One caveat: If you don't have a suitable swap partition, then you will need more RAM. Windows uses the main disk for its swap space, whereas Linux uses a dedicated swap partition. Do you know whether you have a swap partition?

Sorry, I don't have answers for your other two questions about CPU and the PowerMizer.

---

### Post by Ullyxes on 2010-04-09
@Paddy Landau: Thank you so much for this incredible fast answer to one question and yes i have a Swap Partition, it's 2.0GB big. It doesn't matter that you can't answer my other questions, but i think i have to add something: I use the 173.14.20 Driver version of Nvidia

---

### Post by WinterRain on 2010-04-09
Do not be concerned about the RAM usage, as you have plenty available. Memory is there to be used.

You will see advanced settings for your Nvidia card by doing:
```
gksudo nvidia-settings
```

---

### Post by shaka_zulu on 2010-04-09
I think that you are using quite old video driver. There are a few new versions. I can not give you answer on what you asked but i know that newer versions of video driver have many improvements. There have been a lot of questions about how to install new nVidia video driver.

---

### Post by Slim Odds on 2010-04-09
> **Paddy Landau said:**
> ...
I can answer your first question about RAM. Linux uses unused RAM for buffering. Thus, the RAM reading is not comparable to Windows. Your *minimum* RAM needs are less than those on Windows, but Linux uses extra simply because it's available.

One caveat: If you don't have a suitable swap partition, then you will need more RAM. Windows uses the main disk for its swap space, whereas Linux uses a dedicated swap partition. Do you know whether you have a swap partition?
...

Windows also uses file cache like linux. They do it a little differently, but it's very similar. They also report memory a bit differently. The memory reporting by both has created quite a bit of confusion.

Linux can also use a swap file. It's just not the default and is a little slower.

---

### Post by cascade9 on 2010-04-10
> **Ullyxes said:**
>  ASUS Nvidia Geforce 9400GT Silent!

> **Ullyxes said:**
> @Paddy Landau: Thank you so much for this incredible fast answer to one question and yes i have a Swap Partition, it's 2.0GB big. It doesn't matter that you can't answer my other questions, but i think i have to add something: I use the 173.14.20 Driver version of Nvidia

Wrong driver. It should be using 180/185/190/195 drivers.

---

### Post by Slim Odds on 2010-04-10
> **cascade9 said:**
> Wrong driver. It should be using 180/185/190/195 drivers.

I'm running a very similar card (GeForce 9600 GT) and Karmic has it using the 185. Though the 195 should work (according to the Nvidia web site). I believe that the 173 should work, it just won't have all latest features and fixes.

---

### Post by cascade9 on 2010-04-10
> **Slim Odds said:**
> I'm running a very similar card (GeForce 9600 GT) and Karmic has it using the 185. Though the 195 should work (according to the Nvidia web site). I believe that the 173 should work, it just won't have all latest features and fixes.

The 9400GT might 'work' but its not offically supported- 

[http://www.nvidia.com/object/linux_display_amd64_173.14.20.html](http://www.nvidia.com/object/linux_display_amd64_173.14.20.html)

Check the supported products page. The 9400GT was released after the whole 173.xx for FX and -180.xx for everything after date.Its best to avoid running cards released well after the driver if a newer version of the drivers is avaible. 

 Its a good idea to follow the drivers seires spilts that nividia has- 

Vanta up to Geforce 256, Geforce 3- 71.xx
Geforce 2, Geforce 4- 96.xx
Geforce FX- 173.xx
Geforce 6- 200 (current)- 185.xx or higher.

---

### Post by Slim Odds on 2010-04-10
> **cascade9 said:**
> ...
Its a good idea to follow the drivers seires spilts that nividia has- 

Vanta up to Geforce 256, Geforce 3- 71.xx
Geforce 2, Geforce 4- 96.xx
Geforce FX- 173.xx
Geforce 6- 200 (current)- 185.xx or higher.

Totally agree

---

### Post by Ullyxes on 2010-07-30
I tag this as closed or sloved, because now I'm going to install Ubuntu 10.04 LTS. At the moment I still have to use Win XP.

---

