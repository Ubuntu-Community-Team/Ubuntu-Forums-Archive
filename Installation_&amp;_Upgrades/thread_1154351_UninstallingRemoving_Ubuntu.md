---
title: "Uninstalling/Removing Ubuntu"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by BlueHound on 2009-05-09
Hey!

I'm currently running Ubuntu Intrepid Ibex on my laptop. But I wish to make a dual partition consisting of Ubuntu and Windows. Heres the problem, Windows is a very ego-centrical OS and want to be partition #1. So, I need to remove Ubuntu, install windows and then create another partition and put Ubuntu in there. I&#7743; stuck in step 1, removing Ubuntu. I have tried using GParted, but it isn't really working and I think I may be over thinking the problem. All vital data has already been back-uped on a flash drive & the internets, so I just need to get rid of Ubuntu so I can install Windows and then Ubuntu. Theres no need to preserve any data.

So can anybody help me? :)

---

### Post by mikewhatever on 2009-05-09
You need to run gparted from the Live cd and not from Ubuntu installation.

---

### Post by tommcd on 2009-05-09
You should be able to just boot up the Windows install CD and delete and or reformat any partitions you want. Then install Windows to a partition of whatever size you want; and leave the rest of the drive unallocated. Then boot up the Ubuntu install CD and create your Ubuntu partitions in the free space and install to that.

---

### Post by shashi859 on 2009-05-15
here is a simple way to completly removing ubuntu from a ubuntu/windows vista dual boot system without any os disc ,and then recovering those drives and also editing master boot record(MBR) in a easier way.
 
[LIST]
[*]turn on windows vista
[*]just surf for a software **'easybcd' **
[*]download and then install it and run
[*]choose '**manage bootloader'** and in the choose first option which says 'reinstall vista bootloader' ,select write.
[*]after writing successfully then go to my computer --right click on that option--go to manage--disk management--right click on drives in which ubuntu is stored --delete volume.then again format it
[/LIST]that's it . 
 
**IF UR ARE AGAIN SWITCHING TO WINDOWS ?,DON'T DO THAT**
**SEARCH FOR A DISTRO THAT SUITS U OR REPORT A FORUM**

---

