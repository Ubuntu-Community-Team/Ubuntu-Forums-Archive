---
title: "will this computer (dell vostro) run linux"
date: 2019-12-22
forum: Hardware
---

### Post by wolftrax on 2019-12-22
I am going to buy a computer next month for ubuntu studio and I have an offer on a dell vostro 460. which off course is second hand but in good condition. 
it has ntel Core i5-2400 @ 3.10 GHz base, 3.40 GHz boost  and about 500 mg harddrive. 
the system will also have  8 gigabyte RAM and about 500 gigabyte hard  drive in total.   

I was also looking at the dell optiplex but its going to be second hand computer and not laptop this time.

---

### Post by CatKiller on 2019-12-22
Ah, Sandy Bridge. Classic.

You've not said which graphics option it came with. The integrated Intel graphics or the Ati (as was) add-in options should be supported fine by the open source stack. The Nvidia add-in option would be on the Legacy branch of the proprietary driver: it would probably work, but won't get updates.

If it's still got the original hard drive you'll want to swap that out for an SSD.

---

### Post by wolftrax on 2019-12-22
Asus NVIDIA GeForce 210 Silent grafikkort
there are two hard drives in it. 128 GB Samsung SSD + 320 GB Hitachi 7200 RPM HDD

---

### Post by CatKiller on 2019-12-22
Yep, that's supported by the 340 branch of the nvidia proprietary driver. The installer should offer to install it for you, otherwise it's the nvidia-340 package in the "restricted" repository. That machine should be fine as far as I can see.

---

### Post by wolftrax on 2019-12-23
great.

when I searched google on this question I did not find anything other than someone who made a hackintosh with it.   so I thought I might as well ask in here :)

---

