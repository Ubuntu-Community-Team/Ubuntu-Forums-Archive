---
title: "bad battery life due to fglrx video driver"
date: 2011-05-24
forum: Hardware
---

### Post by sgleo87 on 2011-05-24
I just got a new laptop with an ATI video card (Radeon HD 6470M). Battery life in Windows 7 64-bit is almost 6 hours, but in Ubuntu Natty 64-bit it is only 3:15. 

I currently have the latest FGLRX drivers installed with ATI catalyst 11.5. PowerPlay is enabled and set to maximum battery life. In addition I reduced the screen brightness to a minimum, enabled laptop mode and spindown of hard drive.

Powertop shows that one of the top causes for wakeups is fglrx with at least 60 wakeups/sec and I use about 18 watts total. Is this kind of power consumption normal with an ATI Radeon card and is there any way to reduce it?

---

### Post by sgleo87 on 2011-05-25
Nobody else with an ATI card and bad/reduced battery life?

---

### Post by mastablasta on 2011-05-25
Radeon HD 6470M - this would mean that thr drivers you have are very very fresh/new. if they are causing it you will probably need to wait it out until ATI fixes the issue.
 
Top level desktop hardware never really works that good on Linux :-) the manufacturers don't give out the drivers and if they do they are likely still to have some bugs.

---

### Post by sgleo87 on 2011-05-26
Hmm...I figured the fglrx driver would be the same for most ATI cards. According to this thread quite a few people seem to have issues with the fglrx driver and ubuntu natty...

---

### Post by ybytyruzu on 2011-05-26
Hi,
My HP with ATI Mobility RadeonTM HD 4250 and FGLRX use high RAM, start with 400 Mb and after 20 minutes of use 1GB or more. Now I'm using the OpenSource drivers and on idle the RAM use is only 250/300 Mb and for example with Firefox (8 Tabs), VLC full screen, thunderbird, Pidgin, Nautilus open, only 620 Mb. Definitively I will stay for now with the Open Source Drivers. And the baterry life  with FGLRX was 2 Hrs and now 3 hrs

---

### Post by sgleo87 on 2011-05-30
If I use the open source drivers, the wake ups caused by the driver are far less but I use more power overall (25 watts instead of 18 watts with the proprietary driver), so my battery life is an hour less...just the opposite effect than ybytyruzu observed.

---

