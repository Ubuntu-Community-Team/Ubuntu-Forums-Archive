---
title: "Swap: No primary partition"
date: 2013-11-11
forum: Hardware
---

### Post by elang on 2013-11-11
I am running Ubuntu 13.10 64bit on a system with 4GB RAM, dual booting with Windows
  
Most people say that it is good to have swap on a system, and results  in speed, so I used it with my previous Ubuntu installations.

  In my new HDD, I use 3 primary partitions: 1 for Windows OS, 1 for  Ubuntu and 1 for data. The windows system also took up one primary partition for system, and I  have only 4 MBR slots.
Effectively I have no primary partition for SWAP.  I do not know it happened earlier, but back then I had a partition for  swap as well

How can I create swap in my current setup?
I found this article: [http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946), but it refers to an old version of Ubuntu. Also, he asks us to ensure hibernation is working, and that is a problem in Ubuntu 13.10

---

### Post by Yellow Pasque on 2013-11-11
It should go without saying, but make sure you have your data backed up if moving/resizing partitions. (Actually, it's just a good idea in general).

Two options I can think of:
1. Use swap file instead of swap partition (easier and safer)
2. Boot LiveUSB and use gparted to resize the Ubuntu or data partition to make space for an extended partition (which you can then put the swap partition in).

---

### Post by Yellow Pasque on 2013-11-11
Sorry, I forgot the link: [https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F)
Scroll down to where it says "Four-step Process to Add Swap File"

---

