---
title: "Ubuntu won't detect serial mouse"
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by Livino on 2005-07-07
Hi folks,

this is the first time I actually installed Ubuntu anywhere (used the Live CD for a while, and SuSE 9.3 as desktop system). I installed it in this old Duron (700MHz? Not sure) which still uses a serial mouse (not PS/2 or USB, but serial!).

Ubuntu installed without any problems, I can log into it alright - but only by using the keyboard. The mouse pointer is uncontrollable - the mouse won't respond, or rather, it responds but in a completely unprecdictable way.

I've already edited xorg.conf to change the pointing device from /dev/mouse to ttyS0. That made the cursor respond. Uncontrollably.

I've also changed the "simulate 3-button mouse" to false. One doubt I have is that one of the Mouse lines in xorg.conf refers to PS2 (I think it's "device type" or something like that). Anyway, what other modifications should I make to get a simple serial mouse to work with Ubuntu?

What a pain!

Mouse worked fine under Windows and SuSE (this machine had 9.1 installed).

There is no YaST to help me through this, so any input will be highly appreciated.

Cheers!

---

### Post by karthkk on 2005-07-21
Did you change the protocol in xorg.conf to Auto?

---

