---
title: "A very strange GRUB problem"
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by MarcioBarroso on 2006-02-14
Hi,
  
    Let me start by saying I'm completly new to Linux. 
    
    I had a strange situation yesterday:  After a lot of Linux installs, I manage to put both windows and Linux on my SATA HD (partitioned). But, I could only boot using the GRUB floppy disk from Linux installation.
    So I used a software to set the windows partition as the "active" one. So, I could boot on windows without any floppy disk. And when I wanted to boot on Linux, I just had to insert the disk and choose it from the menu. Everything was fine untill...

     ... untill I plug back my old IDE HD (that IDE was plugged during a past Linux installation try, but I decided to unplug it in order to avoid problems at the last install). With the IDE HD plugged, the windows install still works, but the floppy-linux-boot fails. I don't know what is wrong, why does it make any difference for GRUB if the IDE HD is plugged ? 

    thanks in advance

---

### Post by lha on 2006-02-14
When you had only that sata drive, grub saw sata as hd0. Now when you have another drive plugged in, bios names that ide drive as hd0 and sata as hd1. I guess replacing hd0s with hd1s in menu.lst would help.

---

