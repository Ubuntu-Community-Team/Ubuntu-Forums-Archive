---
title: "Dual boot with XP: Location of menu script"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2009-09-10
Ubuntu 9.04

Greetings.

I did something clever (not) and now need to reinstall Ubuntu. I already had a partition setup and Ubuntu had neatly installed in /dev/sda2 (with XP in /dev/sda1).  Some items I do not recall from my previous install:

[LIST=1]
[*]Will it automatically install the GRUB with the XP boot option?  Or do I need to tell it something special to accomplish this?
[*]I am being prompted on where to install the boot loader.  I have picked /dev/sda2 from the menu, the partition where I had previously installed Ubuntu.
[*]Once I have the GRUB menu, where is the menu/script file located? I want to edit it so that XP is at the top of the menu and, thus, the default upon booting.
[/LIST]

Some doc I found ([How to dual-boot XP and Ubuntu]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=4")) tells me that the GRUB menu will be automatically installed. The article omits the [Advanced] option in step 6 of the install process that prompts me with the check-box for the boot loader and the location (mentioned in item 2)

I am sitting here with my PC booted from the live CD, at step 7 of the install.  All I need to do is click on [Install] button. But I am soooo [IMG]http://t0.gstatic.com/images?q=tbn:8AvgaZX1USTVsM:http://www.cksinfo.com/clipart/animals/birds/chickens/ChickenCartoon4.jpg[/IMG]

Advice please?

Thanks much.

---

### Post by x33a on 2009-09-10
1. The installer should automatically pick up the windows partition and add the respective entries into the grub configuration file.

2. you can install the bootloader on the mbr of the drive or into the ubuntu partition also.

3. grub config file is located here
```
/boot/grub/menu.lst
```

---

### Post by rpaskudniak on 2009-09-11
Thank you, Grande. And like the cat you fed yesterday, I am back for more advice.):P

Unfortunately, I didn't get that far. The installation failed and slightly messed up my XP.  I think a full check & repair by Acronis has undone any damage and I will run a full backup over the weekend before I try again.

The was another item I do not recall from my previous successful installation; it may have bearing on my situation.

In one of the later steps, I am prompted (quoting this from memory):
[FONT="Fixedsys"]Do you want to unmount volumes?[/FONT]

This includes the XP/ntfs partitions.  The prompt comes with a warning of what I will be unable to do if I do not unmount.  That seemed innocuous and I feared that unmounting my XP partitions would have ramifications on my XP boot.  Hence, I chose to not unmount.

I also checked the box to format /dev/sda2, the 20 GB partition where I am installing ubuntu.  The reason I did that is that a previous attempt without checking this box failed even more quickly.

With this in mind, my scheme is to retry the install but:
[LIST]
[*]Not to format any of the existing ext2 partitions. (Any data left over from before, leave in place.)
[*]To unmount all volumes, ntfs as well as ext2.
[/LIST]

Advice, please?

(And yes, I have saved my home directory onto a Corsair memory stick.)

Thanks much.

---

### Post by x33a on 2009-09-11
i don't recall any option to unmount other partitions, while installing. but, if the installer recommends that you unmount those (they won't be needed anyway dutring the install), then you should do so.

also, it's better that you format the ubuntu root partition again, so that any leftover files will be cleaned. 

and, you mentioned ext2, well.. i would recommend ext3 or even ext4.

---

### Post by rpaskudniak on 2009-09-11
X33,
Thanks for the advice on the reformatting.  I'll do that, since all my data has been saved anyway.

As for the ext2/ext3 business: At risk of going off thread (but not willing to open a new thread over it), I was advised by my very knowledgeable friend Art that there are stability issues with ext3 and ext4 file when mounted with the option "data=writeback".  At least with ext3, the default mount option is "data=ordered". Google search turned up this [_article_]("http://www.h-online.com/open/Kernel-developers-squabble-over-Ext3-and-Ext4--/news/112937") wherein Linus refers to the writeback behavior of ext3/4 file systems as "insane" and "brain-damaged".

However, again with Art's knowledge, I see I can safely use ext3 (though, when reinstalled, I will peek into /etc/fstab just to be sure of the writeback setting).

When I'm done with this posting, I will search this forum for others' opinions on the issue.

Thanks much for the help and advice.

---

### Post by x33a on 2009-09-11
well i am using ext4 on root with ordered data mode, and ext3 for my storage using writeback mode, and i don't see any problem.

in fact most people use ext3 these days, waiting for ext4 to be more stable.

rest is your choice.

---

### Post by fr4nky on 2009-09-14
will you be able to upgrade from ext3 to ext4 or do you need to reinstall?

---

