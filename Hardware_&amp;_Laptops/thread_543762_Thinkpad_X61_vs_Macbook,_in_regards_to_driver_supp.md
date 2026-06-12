---
title: "Thinkpad X61 vs Macbook, in regards to driver support"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by Nurru on 2007-09-05
I've been using a first gen iBook G4 with Debian since it was released, but it's about time to replace it. I've been looking at the Lenovo X61 as well as a Macbook as possible replacements. The problem is that when I google or search for any info on these two models that I find so much out of date information that I'm not entirely clear if these laptops are fully supported by Feisty, Gutsy or even the mainline kernel. I already played the "Wait till Suspend/Wireless are working" games with my iBook so this time around I'd like to get something that already has the necessary driver support, rather than staring at a bcm43xx status page for months like I did last time (just an example). So basically, can someone with experience with either of these comment on their present usability / support so I can make a better informed purchase?

---

### Post by zeus77 on 2007-09-05
Don't know much of anything about the Macbook, but just got an X61.  I know that the X61 uses the Santa Rosa chipset, and I believe the Macbook does, too.

Driver support for the X61 in Feisty is not great, since the Santa Rosa chipset is not fully supported.  I would guess this applies to both machines, though.  Incomplete Santa Rosa support means that audio, video, and WiFi are crippled or broken for the X61.  Gutsy (to be released in <2 months) is supposed to have much better support.  And most people on these forums running Gutsy on their X61's report mostly positive news.  

Note that people have been able to get video, audio, and wireless working on the X61 w/Feisty, but it won't work out of the box and requires tweaking, recompiling, using things like ndiswrapper, etc.  Out of the box, video does work [it picks the 'vesa' driver], but not with OpenGL or compositing.  

Also, I got the integrated Verizon CDMA Broadband in my X61, which works fine... this makes it a lot easier to survive without WiFi for a couple months... 

zeus77

---

