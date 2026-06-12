---
title: "[SOLVED] Can Grub recognize WinXP automatically?"
date: 2008-08-20
forum: General Help
---

### Post by neur0 on 2008-08-20
Couldn't figure out a better title.
I've been using only Ubuntu since Hardy and now I have a special need for a dual boot with XP.
I resized the partition, and made a small partition for XP. This of course destroyed Grub in MBR, so I used the Super Grub Disk (now I wish I haven't - extremely bad pseudo GUI), and Grub was restored, and I could boot into Ubuntu.
This however meant that there was no XP entry in the menu.lst so I added it manually:

```
title		Windose
rootnoverify	(hd0,1)
makeactive
chainloader +1
```

And this works, but when I upgraded my kernel version today, I got a message (debconf) about menu.lst being manually changed and If I'd like to use the one from the package or leave the old one or see the difference etc. After seeing the difference I think that either way I would lose XP or New Kernel in the menu, so I opted for the "Merge" option (experimental).
Now I have both entries in the menu, but my XP entry is between <old kernel> and <old kernel (recovery)>

My question is this:
Is there some way I can make Grub recognize the XP so it doesn't have problems updating the kernel, and making the XP choice in the menu always second ( or third after <new kernel (recovery)> ) ?

Btw, I did the sudo grub > root (hd0,0) > setup (hd0) after super grub disk, trying to avoid manual editing of menu.lst to get XP, but it didn't work.

---

### Post by sam1948 on 2008-08-20
try to add some more title like this as it shown down here 

title		Windose_0_0
rootnoverify	(hd0,0)
makeactive
chainloader +1

title		Windose_0_1
rootnoverify	(hd0,1)
makeactive
chainloader +1

title		Windose_0_2
rootnoverify	(hd0,2)
makeactive
chainloader +1

title		Windose_1_0
rootnoverify	(hd1,0)
makeactive
chainloader +1

title		Windose_1_1
rootnoverify	(hd1,1)
makeactive
chainloader +1



and so on. dh0 , hd1, hd2, ... as much hard drives that u have
and the second number counts the partitions in every hard drive
(i guess u don't know which one has how many so give every disk the same maximum amount of partitions it will not cause any damage, in the worst case it won't load the xp) 
notice not to touch the ubuntu staff 
u should add those lines at the end of menu.lst

after u did all that , restart u'r computer
try all the new options one of them should load xp 
after finding out which one , go back to menu.lst and remove all the rest
windows_i_j that didnt worked

---

### Post by neur0 on 2008-08-20
Thanks for the reply
But, maybe I wasn't clear: 
I CAN boot into both windows and Ubuntu. I'm just asking if theres a way to make grub add XP in the menu without manually adding it myself and causing problems later for the kernel upgrades. And how to make it always a second (or third) choice.

---

### Post by WRDN on 2008-08-20
> **sam1948 said:**
> try to add some more title like this as it shown down here 

title		Windose_0_0
rootnoverify	(hd0,0)
makeactive
chainloader +1

[etc]


and so on. dh0 , hd1, hd2, ... as much hard drives that u have
and the second number counts the partitions in every hard drive
(i guess u don't know which one has how many so give every disk the same maximum amount of partitions it will not cause any damage, in the worst case it won't load the xp) 
notice not to touch the ubuntu staff 
u should add those lines at the end of menu.lst

after u did all that , restart u'r computer
try all the new options one of them should load xp 
after finding out which one , go back to menu.lst and remove all the rest
windows_i_j that didnt worked

sam1948, there is no point just guessing which partition Windows is on.

In the Terminal, type:

```
sudo fdisk -l
```

This lists all partitions, allowing you to find which one XP is on (this is usually obvious, as the Filesystems are displayed, so look for the 'NTFS' entries).

As for the original question, backup the menu.lst file, and then you can safely alter is manually. If there are entries in the wrong place, or no longer needed, place a "#" before the title line, and it will no longer appear. Could you post your menu.lst file please?

This is part of mine:

> title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Ensure you have the divider between the entries for Linux/ Ubuntu, and the entry for Windows.

Providing the correct formatting is used, it should be updated properly. When requested to update the menu.lst file, it is OK to use the "Use package maintainers version" option (or words to that affect), and it will only update the kernel entries for Ubuntu, not the entire file.

---

### Post by mcduck on 2008-08-20
Just keep the windows entry outside of the section marked as "automagick kernels list" and it shouldn't disappear.

Everything inside the "automagic" area is rewritten automatically during kernel updates, everything outside it should stay.

(The divider entry is not important.)

---

### Post by neur0 on 2008-08-20
My menu (relevant stuff):
```

...

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f45f9970-b757-4d43-aa33-bdb37b072f2b ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f45f9970-b757-4d43-aa33-bdb37b072f2b ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=f45f9970-b757-4d43-aa33-bdb37b072f2b ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Windoz
rootnoverify	(hd0,1)
makeactive
chainloader +1

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=f45f9970-b757-4d43-aa33-bdb37b072f2b ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f45f9970-b757-4d43-aa33-bdb37b072f2b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

... Lots of Kernels

```

Where do you think I should add the divider?
When I looked at the difference, it looked like it was going to erase my XP entry unless I do merge, and thats exactly what I'm trying to avoid in the future.

---

### Post by mcduck on 2008-08-20
Find the line with "### END DEBIAN AUTOMAGIC KERNELS LIST". Then put the Window entry _under_ that line.

Or, alternatively, find the line where the automagick kernels list section starts, and put the Windows entry above it.

As long as it's not inside the automagick section.

(edit: by the way, you can just uninstall the old kernel versions with Synaptic. That would free some disk space & remove their entries from the Grub menu..)

---

### Post by neur0 on 2008-08-20
> **mcduck said:**
> Find the line with "### END DEBIAN AUTOMAGIC KERNELS LIST". Then put the Window entry _under_ that line.

Or, alternatively, find the line where the automagick kernels list section starts, and put the Windows entry above it.

As long as it's not inside the automagick section.

(edit: by the way, you can just uninstall the old kernel versions with Synaptic. That would free some disk space & remove their entries from the Grub menu..)

Ok, makes sense (should have read the entire menu.lst as this is documented in comments)
I did that, and it's OK, but then the Windows came on top (default) so I changed the default option from 0 to 1 and ATM its working as it should. (Windows isn't the second/third option, but it doesn't matter as long as its not default or somewhere far down the list)
I'm marking this as SOLVED, just hope the newest kernel stays default after another upgrade.

---

### Post by mcduck on 2008-08-20
> **neur0 said:**
> Ok, makes sense (should have read the entire menu.lst as this is documented in comments)
I did that, and it's OK, but then the Windows came on top (default) so I changed the default option from 0 to 1 and ATM its working as it should. (Windows isn't the second/third option, but it doesn't matter as long as its not default or somewhere far down the list)
I'm marking this as SOLVED, just hope the newest kernel stays default after another upgrade.
It should, as when the update adds new kernels to the list the latest one will still be the first kernel in the automagick list, thus the second entry in Grub.

But, if you want to confirm that, you could uninstall one (or more) of the old, unused kernel versions. That would cause update-grub to run and re-create the menu.lst..

---

### Post by stormtrooprdave on 2008-08-20
Use qgrubeditor, it makes editing a piece of cake, you can move OS's up and down the order, select the default OS, restore backups, etc.  Its very straight forward

---

