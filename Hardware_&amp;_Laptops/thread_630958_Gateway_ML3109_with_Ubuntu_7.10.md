---
title: "Gateway ML3109 with Ubuntu 7.10"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by Driv3r912 on 2007-12-03
Hello everyone, I am running a Gateway ML3109 laptop notebook, I am having some problems taht weren't answered in the n00b forum.

Let's start off by saying that I have a wireless network - and Ubuntu detects it. It's WEP encrypted at 64 bits, when I go to connect, my laptop crashes and the CAPS LOCK and NUMBER LOCK keys bling, forcing me to restart. How can I resolve this problem.

Also, my computer uses an ATI Radeon Express 200M Series chipset, but I can't use even normal effects, or even use compiz or emerald. Is there a way I can get past this?

Thanks for all the help.

---

### Post by Driv3r912 on 2007-12-04
hmmm... any ideas?

---

### Post by totempole on 2007-12-05
you have to disable the rtl8180 module in /etc/modules/blacklist if im correct. You then use ndiswrapper to load the drivers for windows xp which can be found at [www.realtek.com.tw](www.realtek.com.tw)

Hope this help.

---

