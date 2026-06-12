---
title: "Serial mouse gone crazy"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by Livino on 2005-07-08
Hi folks,

this is the first time I actually installed Ubuntu anywhere (used the Live CD for a while, and SuSE 9.3 as desktop system). I installed it in this old Duron (700MHz? Not sure) which still uses a serial mouse (not PS/2 or USB, but serial!).

Ubuntu installed without any problems, I can log into it alright - but only by using the keyboard. The mouse pointer is uncontrollable - mouse won't respond, or rather, it responds but in a completely unpredictable way.

I've already edited xorg.conf to change the pointing device from /dev/mouse to ttyS0. That made the cursor respond (it was dead before). It responds uncontrollably though.

I've tried to change "simulate 3-button mouse" to false. Didn't help.

One doubt I have is that one of the Mouse lines in xorg.conf refers to PS2 something (I think it's "device type" or something like that). 

Anyway, what other modifications should I make to get a simple serial mouse to work with Ubuntu?

What a pain!

Mouse worked fine under Windows and SuSE (this machine had 9.1 installed).

There is no YaST to help me through this, so any input will be highly appreciated.

Cheers!

---

### Post by Zeroedout on 2005-07-08
hrmm, if you got a screwy logitech mouse, or osme other mouse, just reconfigure xorg and select the appropriate driver. If you're unsure what your mouse is, just keep reconfiguring it with different mouse drivers till it works.

---

