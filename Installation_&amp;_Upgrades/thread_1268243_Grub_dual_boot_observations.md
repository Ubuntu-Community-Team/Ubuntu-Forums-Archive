---
title: "Grub dual boot observations"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by freemanda3 on 2009-09-16
I just wanted to put a few observations out there since I really went through alot trying to get my dual boot laptop back up and running. First of all I  caught the "let me reinstall my 8.04lts system" since I  was having new kernel issues after updating instead of really just taking my time and troubleshooting the thing properly. After that my windows partition was not seen by grub or rather it couldn't be mounted. Secondly I took for granted how easy it was to install a dual boot system on one physical drive but in the end I messed up my boot sector in my windows partition. how, I don't know.   Since I did it for 4 years now. One important thing you need to look at is you need to make sure you find where your grub stage 1 file is located. It can be in the MBR on a partition, either way once you find it then you can run setup for the the physical drive that the results have given you. Also, the fixboot command indicated that my boot sector for windows was corrupted. in the end there were 2 problems that were addressed, installing grub on the wrong partition and a faulty windows boot sector.

---

### Post by raymondh on 2009-09-16
Well done, congratulations.

> **freemanda3 said:**
>  One important thing you need to look at is you need to make sure you find where your grub stage 1 file is located. It can be in the MBR on a partition,

Yes, something I have learned too.  May I add that the boot-info-script can be of huge help in 'investigating' and troubleshooting.  I am a big fan of it .... and it never ceases to teach me something. 

Happy Ubuntu-ing.

---

### Post by louieb on 2009-09-16
> **freemanda3 said:**
> ... but in the end I messed up my boot sector in my windows partition. how, I don't know. ... installing grub on the wrong partition and a faulty windows boot sector.

Yea one caused the other. GRUBS setup command will overwrite a partitions boot sector - Windows - Linux - it just does what it is told to do. 

and +1 for the  [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")  too:KS

---

### Post by presence1960 on 2009-09-17
> **louieb said:**
> 

and +1 for the  [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")  too:KS

I almost always ask for it when someone requests help. Experience has shown me that what someone describes as their setup is a lot of times so far from the actual setup on their machine. The boot info script cuts to the chase and saves a lot of useless going back & forth and speculating.

---

### Post by freemanda3 on 2009-09-17
Yeah, i did use the boot script which I forgot to mention but it just told me what i already knew, which is that primary partition could not be read. another good thing about it is that it gives alot of info. i think the important thing is if you are having problems is to first know how the boot process is supposed to work from a grub perspective and then you can troubleshoot.

---

### Post by raymondh on 2009-09-17
> **freemanda3 said:**
> i think the important thing is if you are having problems is to first know how the boot process is supposed to work from a grub perspective and then you can troubleshoot.

+ 1.

Happy Ubuntu-ing.

Raymond

---

