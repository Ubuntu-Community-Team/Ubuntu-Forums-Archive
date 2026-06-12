---
title: "Need help with Toshiba Tecra 8000"
date: 2006-09-02
forum: Hardware &amp; Laptops
---

### Post by ewl1217 on 2006-09-02
I recently got an old Toshiba Tecra 8000 laptop, which I installed Xubuntu on. Everything runs well, except for two fairly annoying issues.

The first trouble is that sometimes the screen will get noticeably darker and is unusable so dark. This usually happens when trying to run a program (like Frozen-Bubble or SuperTux) in full screen mode (the games work fine when not in full screen mode). I don't know if this has something to do with the xorg driver or something else. I tried the neomagic driver (which should be correct for my video card), but it was terrible looking so I went with the vesa driver (which seems to work fine. The only workaround I know of that works is to simply restart xorg when this problem occurs. I've attached a copy of my xorg.conf, in case that proves useful.

The other issue is that my wireless card wont work. It's some kind of external Belkin card, I'm not exactly sure about the exact model. I have an ethernet card that works (it's actually what I'm using now), but I don't want to bother with a wired connection all the time. Also, on a related note, is there any easy way to switch between wireless networks withing Xubuntu?

That about sums it up. If anyone needs to know more about the specs, don't hesitate to ask.

---

### Post by ewl1217 on 2006-09-04
Ok, I figured out the first issue. After a ton of work with ndiswrapper, I was able to get wireless working. Any ideas on my other problem though?

---

### Post by kinkdxm on 2006-09-08
> **ewl1217 said:**
> Ok, I figured out the first issue. After a ton of work with ndiswrapper, I was able to get wireless working. 
i have the same laptop and some sort of external usb belkin wireless thing. how did you get the wireless to work?

---

