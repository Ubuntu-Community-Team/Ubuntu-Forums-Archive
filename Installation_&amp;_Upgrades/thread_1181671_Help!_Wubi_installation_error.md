---
title: "Help! Wubi installation error"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by daniele.calorio on 2009-06-08
Hi all,

I'm trying to install Wubi in my pc. All goes ok, I downloaded it, restart the pc, select ubuntu in th boot until it stuck at 0% during the final installation with this message "Formattazione dell'area di swap nella partizione num 1 di ho / ..."

Any idea of how can solve it?

Many thanks in advance..

Dan

---

### Post by lasker_341 on 2009-06-10
Same problem here. 
After the firstboot, in the grafic mode it starts checking the installation, it goes wel until it gets to:  

  system is being installed
  swapmemory in partition #1 on host/ubuntu.disks/swap...
  (progress meter stays on 0%)

When I press the powerbutton, it does a normal shutdown. So it does not seem to be frozen, just waiting for something. 

- I installed WUBI under XP on my data-partion ( D: ) FAT32. 
- I have 1GB memory
- I have 4 primary partions on the disk (XP1, XP2, WIN98SE, DATA)
- only XP1 (C) and DATA (D) are visible
- I defragemted the disk and used last version of WUBI

The LiveCD runs fine

I reserved 10GB for ubunti in WUBI 
I noticed that WUBI makes a rather smal swapdisk-file of 256MB

If anyone can help, I would really appreciate it. I am very impressed by the liveCD. If all else failes, I will try normal installation, but for, now I strongly prefer the WUBI solution. 

Is there a way to use WUBI without swapfile? When I delete the swapfile, it creates a new one during first boot. But it still freezes at the same stage.

---

