---
title: "No boot menu displayed but entering Vista directly after Wubi installing"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by rayn0r on 2009-02-03
Hey all
I'm new to Ubuntu linux, and now I'm using Wubi to install ubuntu 8.10 under Vista x64 SP1.

When the Wubi decompress files into the destination disk, it will require reboot. 

After reboot, it was supposed to select Ubuntu in boot menu, but there's no boot menu displayed, and system entered Vista directly.
so I can't finish installing Ubuntu through Wubi.

The boot file of Vista is as below:
[B]There is one entry in the Vista Bootloader.
Bootloader Timeout: 10 seconds.
Default OS: Windows Vista (TM) Business

Entry #1

Name: Windows Vista (TM) Business
BCD ID: {current}
Drive: Deleted Partition
Bootloader Path: \Windows\system32\winload.exe
Windows Directory: \Windows[/B]

And when repairing system by Vista install DVD, it prompts there's problem with boot file, but after reparing the problem, 
there's no change for my issue.

The disk status is as follow:
there's 6 G recover disk, and C,D,E,F are all Dynamic Disk in Vista.

Have anyone met the same issue before?

Thanks!

---

### Post by velizarcho123 on 2011-08-29
> **rayn0r said:**
> Hey all
I'm new to Ubuntu linux, and now I'm using Wubi to install ubuntu 8.10 under Vista x64 SP1.

When the Wubi decompress files into the destination disk, it will require reboot. 

After reboot, it was supposed to select Ubuntu in boot menu, but there's no boot menu displayed, and system entered Vista directly.
so I can't finish installing Ubuntu through Wubi.

The boot file of Vista is as below:
[B]There is one entry in the Vista Bootloader.
Bootloader Timeout: 10 seconds.
Default OS: Windows Vista (TM) Business

Entry #1

Name: Windows Vista (TM) Business
BCD ID: {current}
Drive: Deleted Partition
Bootloader Path: \Windows\system32\winload.exe
Windows Directory: \Windows[/B]

And when repairing system by Vista install DVD, it prompts there's problem with boot file, but after reparing the problem, 
there's no change for my issue.

The disk status is as follow:
there's 6 G recover disk, and C,D,E,F are all Dynamic Disk in Vista.

Have anyone met the same issue before?

Thanks!

The same problem... And the problem occurs in the new ubuntu releases, after 10.10.. Is any way to resolve? on XP machine there IS a boot menu, but in Vista/7 not...

---

### Post by uRock on 2011-08-29
Please post in the Wubi Megathread for best results. [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

