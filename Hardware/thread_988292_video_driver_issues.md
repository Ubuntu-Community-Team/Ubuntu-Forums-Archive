---
title: "video driver issues"
date: 2008-11-20
forum: Hardware
---

### Post by tanis143 on 2008-11-20
Ok, I've read through a few topics and so far I can not figure this out. I'm fairly new to ubuntu (have tried other versions off and on) and still very new to Linux in general. Here is what I'm using:

Ubuntu 8.10
Abit KR7A Raid
AMD 1800+
512 megs ram
Nvidia FX 5200


I've downloaded and installed (I think) the latest Nvidia Linux drivers (version 173). When I goto the System> Admin > Hardware Drivers it comes up and shows the 173 as activated and in use as well as an older version which is not in use. However, when I try to use System> Admin> Nvidia Xserver Config it tells me I'm not using an Nvidia driver. Also, I can go no higher than 800 x 600 resolution. What am I doing wrong? :confused:

---

### Post by tanis143 on 2008-11-21
I guess no one can help with this issue :(

---

### Post by marshall.robert on 2008-11-21
i suggest going to Applications -> Add/Remove and then searching for 177 and using that. thats how i did it because the Hardware Drivers thing doesnt do s**t.

---

### Post by tanis143 on 2008-11-21
Well, found the issue. Seems that 8.10 and 173/177 do not play with geforce4 and below chipsets, so this fx 5200 wont work. Might try an ATI video card I've got spare, if that doesn't work I'll just drop back down to an older version of Ubuntu, probably a 7.x series as I know this card worked well with it.

---

