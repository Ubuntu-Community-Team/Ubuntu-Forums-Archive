---
title: "Xp is not detected during Ubuntu 9.04 install"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by gen2002 on 2009-08-29
I'm new to ubuntu..
Trying to install ubuntu 9.04 32bit desktop

I choose specify partition manually...

problem was while trying to install following this steps
[http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml)

on the Hard disk partitioning stage.. I notice Xp was not detected.. so I cannot install ubuntu coz I think it will mess up xp's boot loader and I wont be able to boot windows again..
So how do I install ubuntu to dualbooth with windows..

the disk is partioned this way..
drive c(ntfs) --- xp bootloader is here(primary Partition)(using this as xp's swapDrive)
drive d(ntfs)--- Xp is installed hert
drive e(ntfs)--- contain Personal Files
free space --- plan to install ubuntu here

c,d,e and free space are logical drives( I only have one HDD)

thanks..

---

### Post by mikewhatever on 2009-08-30
What do you mean XP is not detected? Why does it matter? Since you want to use the free space, and aren't going to resize the Windows partition, it doesn't matter what the installer 'thinks' of it. Neither the partitioning program nor the installer 'mess'  with Windows bootloaders. The installer will overwrite the MBR, which belongs to the hdd and not to Windows, and will hopefully add an entry for Windows to the Ubuntu boot loader. If that doesn't happen, it's not very hard to add it manually, just post a help request.

---

### Post by dandnsmith on 2009-08-30
> **mikewhatever said:**
> Neither the partitioning program nor the installer 'mess'  with Windows bootloaders. The installer will overwrite the MBR, which belongs to the hdd and not to Windows
Not entirely true - it contains boot code which gets replaced by grub boot code.

 > and will hopefully add an entry for Windows to the Ubuntu boot loader. If that doesn't happen, it's not very hard to add it manually, just post a help request.
That is certainly true, but it's worrying that XP isn't detected as it may have deeper implications.

I'd back up everything, and include the boot sector especially, and then try it (but I'm used to recovering systems when something goes wrong)

---

