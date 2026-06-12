---
title: "[SOLVED] Final at last!"
date: 2008-08-29
forum: General Help
---

### Post by Yezinki on 2008-08-29
Hi there,

I have finally decided to install Vista only on Dell  laptop & XP MCE 2005 + Ubuntu Hardy Heron dual boot on Sony desktop VGC-LS1.

Following are my queries:

1. How do many & what sizes of partitions should I make for the dual boot..HD is WD 250 GB.............my thinking was
 
     a. C: Primary: NTFS: XP  MCE.
     d. D: Logical: NTFS: Data
     e. E: /root: ext3.
     f. F: /swap.
     g. G: /home...& Vbox in it.


       
     100 GB total NTFS XP.
     20 GB /root.
     4 GB swap.
     120 GB /home?

     Is that OK.
     

2. At this moment I am using Kubuntu Hardy Heron on this Sony machine........cant connect via wireless..It could when I had installed Ubuntu on this Sony?

3. How would I be able to use my Sony Vaio's, integrated Z-star Micro Corps cam in Pidgin..is that possible?

Kindly guide me as I finally make  the dual boot of XP & Ubuntu hardy.......as am a new bie & shall keep bothering you......which I hope you wont mind.

Regards!

---

### Post by 3rdalbum on 2008-08-29
1. Reduce your swap - 4 gigabytes is way too much. Try 1 gigabyte, tops.

2. Pidgin doesn't support cameras, but Kopete and aMSN do. I don't know if your camera is supported.

Make sure you install your Windows first, and then Ubuntu. At the screen in the Ubuntu installer where it says "Erase entire disk /dev/sda" and "Erase partition /dev/sda1" or something similar, use the "Manual Partitioning" option INSTEAD.

---

