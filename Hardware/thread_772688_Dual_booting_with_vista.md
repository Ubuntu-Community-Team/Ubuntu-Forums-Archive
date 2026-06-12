---
title: "Dual booting with vista"
date: 2008-04-28
forum: Hardware
---

### Post by Niklas93 on 2008-04-28
Hi. I've installed ubuntu 7.10 on my maschine which was already running vista at the time. I used the tool build in the installer to resize the vista partition and to make a new ex3 partition for ubuntu and a swap partition. Now my problem is that when my installation was done i couldn't see vista in the grub menu. I don't know how to set the vista partition active, so can anyone please tell my why it is so and more important how do I set vista active?

---

### Post by Yellow Pasque on 2008-04-28
You resized your Vista partition? Not good....
[http://www.pronetworks.org/forum/about78184.html](http://www.pronetworks.org/forum/about78184.html)

---

### Post by Alldan on 2008-04-28
I have both Ubuntu & Vista on my computer too.
For me Hardy configured Grub correct and i don't have problems with dual boot, but i don't resized partitions.
I had another distribution installed before and i experienced your problem
Question: you can mount windows partition in ubuntu? If affirmative try Temujin's link. To edit grub configuration file it's easier to use 
ALT+F2 and type gksudo gedit
In my case vista started but crushed very quick. I used Vista DVD and repaired vista installation without losing data but it will erase bootloader. To restore Grub you can use Ubuntu livecd

---

