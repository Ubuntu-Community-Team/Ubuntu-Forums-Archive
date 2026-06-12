---
title: "Partition Help"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by drifter2502 on 2009-07-28
Currently I am using win xp on my pc. It is partitioned C and D that was configured by the shop when I purchased it and I do not know how exactly that was done. C holds all the os and  program files and D has all my files,music,pictures,documents etc.
I want to place all of my files onto the external drive from D and use the space on D for ubuntu 9.04. I am not sure if I can just install ubuntu to D without re-partitioning first. I would be pleased to have some guidance what to do. I have 5 gb left on C and will have about 40 on D when I take my files off it. I do not have the xp disc so must tread carefully. I do not want to lose my xp programs on c.

---

### Post by wojox on 2009-07-28
Welcome this should help out:

[https://help.ubuntu.com/9.04/switching/index.html](https://help.ubuntu.com/9.04/switching/index.html)

---

### Post by lindsay7 on 2009-07-28
This too,



[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by drifter2502 on 2009-07-29
Thank you but I am still quite anxious about starting the process. How will I know for sure which is the D partition (currently holding all my own files on xp and where I want ubuntu to work from) from the below description? Will it be marked up as hda 2 or primary 1 or something else?  :-
  Quote:  You are probably used to how Windows represents disks. Your first hard drive partition is usually the C: drive, although this can be changed. Linux has a fixed way of referring to disks, which cannot be changed.

Devices are named differently too:

    *

      The first Master IDE hard disk is called hda.
    *

      SCSI, SATA and USB are referred to as sd.
    *

      Each primary partition is numbered 1 to 4.
    *

      Each logical partition is numbered from 5 upwards.

Hence the first logical partition on the master IDE drive will be hda5.

---

### Post by dandnsmith on 2009-07-29
That quote represents info about drive naming which is now out-of-date.
Both PATA (IDE) and SATA drives now show as sd*x*, so the first logical partition on the master IDE drive will be sda5.

To find out which is which, you may need to use the disk management in Windows: use Control Panel|Admin Tools|Computer management, and select the disk management. This will give a display of the partitions and disks.
You can then relate this to the installer info.

HTH

---

### Post by lindsay7 on 2009-07-29
Here is the walk through,


[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by drifter2502 on 2009-08-01
> **lindsay7 said:**
> Here is the walk through,


[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)


Thanks. I think I should go with the Guided-resize outlined in the tutorial from #6 lindsay 7 but before I do so here is my current  HD set-up:-
C Boot.NTFS        39GB Disk 0-free 15,43GB.
D (system)NTFS  37GB Disk 0-free 19.64GB
Wubi                                      1           7.46GB

Wubi being an exe file in C. (don't know why it shows 1)

So,based on the above details will it be ok , assuming I delete all my files on D and delete Wubi in C, to choose a partition of 50% Win xp and 50% Ubuntu ?

I think I now have the courage to go ahead but is there any other advice you could suggest before I jump in the water?!

---

### Post by la3875 on 2009-08-01
I recommend you see this site as well - [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

It has been a great resource for me.

Best!

---

