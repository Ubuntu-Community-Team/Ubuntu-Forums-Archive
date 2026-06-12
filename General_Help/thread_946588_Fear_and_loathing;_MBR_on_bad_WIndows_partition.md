---
title: "Fear and loathing; MBR on bad WIndows partition"
date: 2008-10-13
forum: General Help
---

### Post by Pantherman on 2008-10-13
My MBR is on my Windows XP partition, which is corrupt now and slowly degrading and taking everything with it. How do I re-install Windows, and keep the MBR intact, or can I somehow copy it and re-install it with the new windows installation so that I can still boot into linux?

Pantherman

---

### Post by TeXtonyx on 2008-10-13
Viva Las Vegas! I'm not sure that you know your diagnosis is accurate. In any case
you have some options. You can run your XP Recovery Console (R) and do a
fixmbr. You can do a repair install and put Windows in C:\Windows.0 but this can
turn into a pita. Either of those methods rewrites the MBR. If you already have Linux
installed to the MBR it will be overwritten. If you do not have (K)Ubuntu (this is easier
than OpenSuse for newcomers) installed, then I recommend you leave a goodly
chunk of GBs unallocated on your drive, and then choose largest unallocated space 
during the Ubuntu live cd install. During Step 7, of that live install, choose Advanced
and uncheck hd0 (hd0 is the choice to install to the MBR). Instead choose install
grub to the boot partition which you have to know its number such as sda2. Then
you can use Bootpart to operate so you can boot Ubuntu from the XP boot.ini.

[http://ubuntuforums.org/archive/index.php/t-499904.html](http://ubuntuforums.org/archive/index.php/t-499904.html)
[http://forums.majorgeeks.com/showthread.php?t=108021](http://forums.majorgeeks.com/showthread.php?t=108021)

Another way if you are less geeky is to reinstall (or first install)  and leave the
default in place, hd0, which will write to the MBR of the drive. Then XP will show
up as a choice from the grub menu instead of the boot.ini menu. If you have time
invested in a current Linux partition, it is possible to reinstall grub without messing
with your whole Linux install. I recommended the use "largest unallocated space"
during the Ubuntu install because you won't overwrite your XP partition. That
means you have done any resizing of partitions before using the Ubuntu live cd.

There is an alternative way to resize partitions using Linux but that may require
more expertise from you. Use the way you know best. XP deletes partition with
Computer Management->Disk Management and Ubuntu with a partition editor
which you can run first from the live cd. Deleting a partition renders it into 
unallocated space (not free space within a used partition). Don't delete the XP
partition once you have it restored to health. One needs to be a bit careful.

---

