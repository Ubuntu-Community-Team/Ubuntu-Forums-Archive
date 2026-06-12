---
title: "Windows 7 Full (Ubuntu installed First)"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by okayneil on 2009-08-19
Hey guys, sadly a Windows question. Im one of the lucky/unlucky few who have access to msdn alliance which contains the full version of windows 7. Currently I have a dual boot ubuntu (installed first) windowsXP. I want to add a windows 7 install. I was going to follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=1035999") but wanted to ask first if there were any major things i need to watch out for?

Should just be a case of : 

1. Partition disk with gparted.
2.    Install Windows7.
3.    Re-install Grub.
4.    Edit Grub to List Windows 7.

Update***

[I]Installed windows 7 professional using the tutorial above, worked like a charm, no problems except a small one. 

When editing the grub menu to make a new slot for windows 7 pointing to its correct installed location it will not boot, but when i select the windows xp grub menu it takes me to a screen which allows me to choose xp or win 7. 

Not sure what to think of that, but overall seems good.[/I]

---

### Post by Copernicus1234 on 2009-08-19
I dont know. Windows 7 doesnt seem too good at coexisting with others since its a Microsoft product. XP works pretty good, but I have seen users having problems with 7.

---

### Post by thunk77 on 2009-08-19
Presumably you are correct, but who knows what wonderful things microsoft has in store for you..

---

### Post by okayneil on 2009-08-19
> **thunk77 said:**
> Presumably you are correct, but who knows what wonderful things microsoft has in store for you..

Some are saying it works well others not. Fingers croassed :)

---

### Post by SuperSonic4 on 2009-08-19
If you have a spare drive install it there :p

If not pray

---

### Post by confused57 on 2009-08-19
> **okayneil said:**
> Hey guys, sadly a Windows question. Im one of the lucky/unlucky few who have access to msdn alliance which contains the full version of windows 7. Currently I have a dual boot ubuntu (installed first) windowsXP. I want to add a windows 7 install. I was going to follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=1035999") but wanted to ask first if there were any major things i need to watch out for?

Should just be a case of : 

1. Partition disk with gparted.
2.	Install Windows7.
3.	Re-install Grub.
4.	Edit Grub to List Windows 7.

This should work fine, I've installed Windows 7 RC on 2 different computers dual booting with Ubuntu. On the first computer I didn't pre-format an ntfs partition & also ended up with a 100 Mb boot partition added automatically, in addition to the Win 7 partition.  The 2nd computer, I made a ntfs partition(25 Gb) beforehand with gparted, reformatted to ntfs during the Win 7 install & didn't get the 100 Mb boot partition added.  Both dual boots working great.

---

### Post by okayneil on 2009-08-19
> **confused57 said:**
> This should work fine, I've installed Windows 7 RC on 2 different computers dual booting with Ubuntu. On the first computer I didn't pre-format an ntfs partition & also ended up with a 100 Mb boot partition added automatically, in addition to the Win 7 partition.  The 2nd computer, I made a ntfs partition(25 Gb) beforehand with gparted, reformatted to ntfs during the Win 7 install & didn't get the 100 Mb boot partition added.  Both dual boots working great.


Good to hear!

What are my chances of this going wrong?

---

### Post by running_rabbit07 on 2009-08-19
Just remember your backups.

---

### Post by okayneil on 2009-08-19
> **running_rabbit07 said:**
> Just remember your backups.

All files, grub....bookmarks hehe what else?

---

### Post by okayneil on 2009-08-19
Installed windows 7 professional using the tutorial above, worked like a charm, no problems except a small one. 

When editing the grub menu to make a new slot for windows 7 pointing to its correct installed location it will not boot, but when i select the windows xp grub menu it takes me to a screen which allows me to choose xp or win 7. 

Not sure what to think of that, but overall seems good.

---

### Post by Mark Phelps on 2009-08-20
> **okayneil said:**
> When editing the grub menu to make a new slot for windows 7 pointing to its correct installed location it will not boot, but when i select the windows xp grub menu it takes me to a screen which allows me to choose xp or win 7.
That's because Windows 7, like Vista, installs its boot loader files into the first NTFS partition it finds on the disk, in this case, your XP partition.  This means that if you every remove XP or reformat that partition, Windows 7 will not boot.  Do yourself a favor and use the option in Windows 7 to create a recovery CD,  You can use that later to restore the boot loader if you decide to remove XP or reformat that partition.

---

### Post by okayneil on 2009-08-20
Can you switch the location of the bootloader?

---

### Post by louieb on 2009-08-20
> **okayneil said:**
>   but when i select the windows xp grub menu it takes me to a screen which allows me to choose xp or win 7. Not sure what to think of that..

Thats the MS way of setting up dual boot. The newer puts it boot loader in the older and does not put a boot loader in itself. 

With XP and Vista there are recovery disks floating around on the net. I know MS has one available for Vista.  Win 7 is still so new that I haven't even looked. Heck I can't even find the drivers for my HP printer or sound chip:(

---

### Post by Mark Phelps on 2009-08-20
> **louieb said:**
>  Heck I can't even find the drivers for my HP printer or sound chip:(
Try Googling for the Microsoft Update Catalog.  Allows you to search the entire MS update catalog for drivers.  Of course, you must be running IE in order to use it (no surprise there!).

---

### Post by presence1960 on 2009-08-20
> **okayneil said:**
> Hey guys, sadly a Windows question. Im one of the lucky/unlucky few who have access to msdn alliance which contains the full version of windows 7. Currently I have a dual boot ubuntu (installed first) windowsXP. I want to add a windows 7 install. I was going to follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=1035999") but wanted to ask first if there were any major things i need to watch out for?

Should just be a case of : 

1. Partition disk with gparted.
2.    Install Windows7.
3.    Re-install Grub.
4.    Edit Grub to List Windows 7.

Update***

[I]Installed windows 7 professional using the tutorial above, worked like a charm, no problems except a small one. 

When editing the grub menu to make a new slot for windows 7 pointing to its correct installed location it will not boot, but when i select the windows xp grub menu it takes me to a screen which allows me to choose xp or win 7. 

Not sure what to think of that, but overall seems good.[/I]
That is exactly how it is supposed to work if you install a second version of windows on a machine. Microsoft has it set up that way. Call Redmond to complain. just leave the XP entry in menu.lst and choose which version of windows from XP.

---

