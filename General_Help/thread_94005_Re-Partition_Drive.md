---
title: "Re-Partition Drive"
date: 2005-11-23
forum: General Help
---

### Post by dwessell on 2005-11-23
Hey all.. I'm trying to shrink my windows partition on this machine, and am having a small issue.. When I boot using the live CD into Ubuntu, and try and run gparted.. The swap is in use (Only one HD) so I can't repartition the one drive.. How can I unmount that swap long enough to repartition?

Thanks
David

---

### Post by aysiu on 2005-11-23
Swap being in use shouldn't stop you from shrinking a Windows partition. Just make sure the Windows partition is unmounted.

---

### Post by dwessell on 2005-11-23
Hmm.... The windows partition is unmounted (At least, I looked that the properties of that drive from in gparted, and it stated that it was unmounted). 

Once I resize the drive, it tells me that a part of it is being used, and I need to reboot (Sorry, I dont have exact languange, I'm away from that computer today). At first I thought this meant it would all happen on the reboot, but after the reboot, nothing appears to have happended.. Looking at the list of partitions, the only one mounted was the swap, so I 'assumed' that was the cause of the trouble..

Thanks
David


[QUOTE=aysiu]Swap being in use shouldn't stop you from shrinking a Windows partition. Just make sure the Windows partition is unmounted.[/QUOTE]

---

### Post by aysiu on 2005-11-23
To be perfectly honest, QTParted and GParted are good tools, but they don't always work. I've found, oddly enough, Mandriva's DiskDrake to be the most reliable free partitioning tool.

I don't actually *install* Mandriva--I just use the partitioning part of the installation, then reboot when I'm done.

---

