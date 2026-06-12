---
title: "Dual Booting?"
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by Im_Just_GrayT on 2006-01-15
Hello, I recently decided to reformat my hard drive. while doing this i decided to leave about 14gb off my windows partition in case i wanted to install linux. well ive decided that i want to install linux now, and i would like to keep windows at the moment(i would love to just completely switch in the future)

 so what i have is a dell pc currently running windows xp home. the hard drive is divided into 2 partitions. one of wich is still "raw" (i think) and the other is my windows partition. I guess im just looking for someone to walk me through the installation and dual booting process because im afraid i'll do something really stupid.

If anyone is willing to help. it would be greatly appreciated. Thank you!:p

---

### Post by eyebrowman92 on 2006-01-15
your best bet is to use the ubuntu install cd (if you have one) and to use the partitioner. when it gets to the partitioner select manually edit partition table. then select create new partition. then select the partition on your hd that is "raw" and give it a filesystem of ext3 (that is what i use). then select the mount point to be / and and make it a primary partition and give it a bootable flag.  then select create or something like that. after that select write changes to disks, and the installer will install ubuntu to the empty space.

---

### Post by aysiu on 2006-01-15
See the fifth link of my signature--it's very detailed... screenshots and explanations.

---

### Post by Im_Just_GrayT on 2006-01-15
whoa that was fast. i just posted this like 30mins ago. you guys rule. thanks for the help. I will repost after i try (and hopefully succeed) 

Also, the cds i have for ubuntu are version 5.04. i noticed that the newest is 5.10. is this a problem?

oh and one more thing, do i need a boot manager? so i can tell my computer wich OS to boot everytime i restart it? just wondering. thanks again for the help!:D

---

### Post by Ptero-4 on 2006-01-15
You don't need a boot manager. Ubuntu comes complete with a multi-OS boot manager.

---

### Post by Im_Just_GrayT on 2006-01-15
a question about resizing the windows partition. when i do a defragment it still shows some data over on the right hand side (its not all packed together) although the total used space is about 22gb. if i resize it to about 25gb will it move that stuff back towards the other stuff or work around it or what? is it safe to do that? thanks

Ive also been reading about wireless card support since im currently using one. I have a card made by D-link if anyone knows if thats supported or not.

---

