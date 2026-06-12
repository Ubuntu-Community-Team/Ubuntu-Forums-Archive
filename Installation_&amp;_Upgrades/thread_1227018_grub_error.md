---
title: "grub error"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by praveen1889 on 2009-07-30
I have windows xp and ubuntu 9.04 in my computer. i installed first xp and then ubuntu,while installing ubuntu,they asked from where to boot,i changed it to the my windows xp drive,not the master boot record,but when i am trying to access my windows xp ,it displays as no such device,so please help me

---

### Post by stlsaint on 2009-07-30
If this is too much i am truly sorry but you may want to start from the beginning and learn all you can about partitions first before you start dual booting!!

looks like you overwritten your winxp partition. during ubuntu install either you use the entire disk...which will wipe any other OS you have installed! or you use manual selection in which you set where to boot and how much swap to use and whats goin to be your boot (/,ext3 or ext4)! now its up to you how you split up your partitions. if you want to dual boot than install xp first, setup your partitions thru disk management, then install (from disc) ubuntu and set it to boot from your empty partition. DO NOT CHOOSE TO BOOT FROM YOUR WINDOWS PARTITION OR YOU Will wipe it clean.  during the ubuntu install you must select 2 seperate partitions within the original partition. confusing i know but stay with me...when you select to manualy install you must select this: CREATE PARTITION>(ASSIGIN AT LEAST 1GB OR 1024 KB) FOR YOUR SWAP>CHOOS DROPDOWN MENU-USE AS /SWAP!!! STILL THERE...THEN CREATE ANOTHER PARTITION TO INSTALL ROOT FILE SYSTEM...(THIS WILL BE THE REST OF THE PARTITION YOU ALLOCATED THATS NOT IN SWAP MEMORY) SO...CREATE PARTITION>DROP DOWN MENU> / > EXT3!

---

