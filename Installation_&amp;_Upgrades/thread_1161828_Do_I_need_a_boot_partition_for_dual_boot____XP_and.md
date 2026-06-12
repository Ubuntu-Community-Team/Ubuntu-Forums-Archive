---
title: "Do I need a /boot partition for dual boot ?   XP and Ubuntu"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by vur246 on 2009-05-17
I would like to install ubuntu on my DEll Inspiron 7500 laptop (currently has XP on it). It's an old laptop and I wonder if there is any tool I can download and check if I need to create a separate /boot partition at the beginning of my 60G harddrive to escape 1024 cyl limitation. 

I couldn't find a decisive answer in manuals and forums so that's I hope there is something I can download and run . My BIOS is Phoenix 4.0 rev 6.0 which looks like it supports it, but if I am correct it's not enough I also need support in chipset and drive itself 

Thanks in advance for the help

---

### Post by labinnsw on 2009-05-17
> **vur246 said:**
> I wonder if there is any tool I can download and check if I need to create a separate /boot partition at the beginning of my 60G harddrive to escape 1024 cyl limitation.

I don't know of any such tool but I have a very antique dell myself and I was able installed both Ubuntu and Xubuntu the same way I do on the PC I upgraded in December. No need for a separate /boot partition. I am still using Ubuntu 8.04.

Is it a SATA drive?

---

### Post by briandu on 2009-05-17
You do not need to have a separate /boot as you can just use the partition as a / together with the swap in the extended drive,

Then you must use grub install. You can chain load in Windows but folks do experience problems later when they update XP. Rather have the boot process outside of the OS'.

---

### Post by vur246 on 2009-05-17
Thanks for the responses

I've just installed 8.10 with no problemm, dividing HDD 50/50 between xp and ubuntu - each 30G. Double boot works fine so looks like 1024 cyl limit not a problem. My laptop is from 2000 .

---

