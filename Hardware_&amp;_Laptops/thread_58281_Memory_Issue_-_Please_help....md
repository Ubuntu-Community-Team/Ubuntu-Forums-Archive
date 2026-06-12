---
title: "Memory Issue - Please help..."
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by recklessray on 2005-08-19
Hi there. this is my second post with regards to the RAM problem i have in ubuntu. I have a P4 2.8, 1 gig DDR, MSI board, DVDRAM, all connected up to a wired router for internet. Everything works like a dream. im very, very impressed with linux (ive only recently taken the plunge from XP), and my few snags like getting my HP PSC 950 scanning were quickly overcome by reading the forums here, so thanks. 

My last big problem is RAM detection. I have 1 gig installed. This is fine when i boot from Knoppix and when i had XP, but under ubuntu it only says 377.4 in the system monitor... I posted last week and some gentlman suggested i upgrade the kernal to the 686 version, which i did, but aside from booting up a bit more speedily, there is no more ram recognised. This is a real headache for me, ive tried all the forums and googled till im passing out, but cant find the answer,.... can anyone help please????

many thanks, ray :)

---

### Post by blastus on 2005-08-19
I also have 1Gb and Ubuntu only sees 885Mb. I also read about upgrading the kernel but I don't know how to do that. The other thing too is that if I mess around with the kernel I understand (and I could be wrong) that I would have to reinstall the nVidia drivers and recompile the drivers for my Lucent WinModem.

RAM is such a basic thing in a system that I don't wanna have to mess around with stuff to get an OS to use it. It should just recognize and use my 1Gb straight out-of-the-box. Maybe we need an i686 ISO or something I'm not sure? I eventually plan on bumping the RAM on this machine to 2Gb. This really needs to be fixed!

---

### Post by AnythingBut on 2005-08-20
[QUOTE=recklessray]Hi there. this is my second post with regards to the RAM problem i have in ubuntu. I have a P4 2.8, 1 gig DDR, MSI board, DVDRAM, all connected up to a wired router for internet. Everything works like a dream. im very, very impressed with linux (ive only recently taken the plunge from XP), and my few snags like getting my HP PSC 950 scanning were quickly overcome by reading the forums here, so thanks. 

My last big problem is RAM detection. I have 1 gig installed. This is fine when i boot from Knoppix and when i had XP, but under ubuntu it only says 377.4 in the system monitor... I posted last week and some gentlman suggested i upgrade the kernal to the 686 version, which i did, but aside from booting up a bit more speedily, there is no more ram recognised. This is a real headache for me, ive tried all the forums and googled till im passing out, but cant find the answer,.... can anyone help please????

many thanks, ray :)[/QUOTE]
 Does "cat /proc/meminfo" report the same thing?

---

### Post by JELaVallee on 2005-08-22
I'm experiencing the same issue with 2Gb on my system...  :mad: 

I did see somewhere someone noting that the 386 build lacks hi-mem support. Which would explain the 885MB block...

Does anyone have concise instructions on how to rebuild the kernel to include such support?

Thanks,
Etienne

---

### Post by JELaVallee on 2005-08-22
Just found this thread which explains this issue and it's resolution very well:

[http://ubuntuforums.org/showthread.php?mode=hybrid&t=57492&highlight=memory+885](http://ubuntuforums.org/showthread.php?mode=hybrid&t=57492&highlight=memory+885)

Hope that helps!

cheers,
Etienne

---

