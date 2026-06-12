---
title: "Windows won't recognize the Hard Drive"
date: 2008-09-06
forum: General Help
---

### Post by Edigido on 2008-09-06
When I had used the Gparted live CD in order to resize/delete the partition I then modified the main partition that was ubuntu controlled (/dev/sda1).  Then when I made a new partition and didn't format it, I tried to re-install, but Windows 2000 (it's the original that I'm going to upgrade) still wouldn't recognize the Hard Disk.  I'm not sure if I had skipped a step, or if I'm taking the entirely wrong approach to solving this problem.  I don't wanna use Virtual Box, because that won't get the games as well as many of the programs that I need.  I've used it before, and it doesn't work as well as the real thing.  Thank you for your time ^_^

---

### Post by ryanhaigh on 2008-09-07
If your windows 2000 CD doesn't detect the hard drive at all (this is different from not detecting the partitions) it sounds as though the ide/sata controller on your board is not recognised. For windows XP installation you can press F6 at some stage to load drivers from a floppy disk, there may be something similar in the Win 2000 setup. In order to use this you will need to find drivers for the mainboards controller that are compatible with win 2000.

---

