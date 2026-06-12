---
title: "Windows XP broke GRUB"
date: 2005-11-07
forum: General Help
---

### Post by Confused Fishcake on 2005-11-07
I was happily using a dual boot Ubuntu/XP system, when I tried to add an extra windows xp partition (Optimised for gaming etc.) However, now I have to select between the two windows installations with the default program. How do I reinstall GRUB? (I can still read/write the ubuntu partition for windows)

---

### Post by tonysathre on 2005-11-07
put in the ubuntu install cd and get to the partitioning part, but dont change anything, then go back to the main menu and select install grub

---

### Post by 23meg on 2005-11-07
[http://www.ubuntuforums.org/showthread.php?t=56668](http://www.ubuntuforums.org/showthread.php?t=56668)
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by Confused Fishcake on 2005-11-08
Thanks for that, I sort of fixed it, but (wait for it), when I boot up my pc, I get GRUB's choice of Windows XP, Ubuntu, Memtest, and Recovery mode. However, I have two windows XP installs on my HD, so when I select XP, it loads the windows boot loader, allowing me to choose between the two XP partitions. However, this is not what I want at all. Just to clarify, this is how I have partitioned my hard drive:

1) Windows XP, used by everyone in my family
2) Windows XP, optimised for gaming, only used by me
3) Ubuntu, used only by me as my main OS

---

### Post by _MiniMe_ on 2005-11-08
Open /boot/grub/menu.lst and add a new entry for your second windows partition. If you scroll down to the bottom you should see the entry for your first Windows partition. Copy that and change "root		(hdx,x)"  to whereever your Windows partition is located. Remember that "hd0" in grub is the first HDD, "hd1" the second. Same with partition counting. 

For example: (hd1,5) in menu.lst is /dev/hdb6 in linux.


hope this helps

---

### Post by paddyg on 2005-11-08
[QUOTE=Confused Fishcake]Thanks for that, I sort of fixed it, but (wait for it), when I boot up my pc, I get GRUB's choice of Windows XP, Ubuntu, Memtest, and Recovery mode. However, I have two windows XP installs on my HD, so when I select XP, it loads the windows boot loader, allowing me to choose between the two XP partitions. However, this is not what I want at all. Just to clarify, this is how I have partitioned my hard drive:

1) Windows XP, used by everyone in my family
2) Windows XP, optimised for gaming, only used by me
3) Ubuntu, used only by me as my main OS[/QUOTE]

Grub can't boot windows directly unless you have two windows loader on separate disks. Grub just chain-loads, and then windows reads the boot.ini--which i think is on your Windows # 1 (family use)--and that's what you see on the screen.

Just take a look here for more info:
[http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)

---

### Post by Confused Fishcake on 2005-11-09
I have deleted the second wimdows partition, and GRUB can boot to either XP or Ubuntu. I still want to install another XP. Is there any way to hide the existing installaton so that It gets its own bootloader, and can then be booted by GRUB? Anyone know any other way to do it?

---

### Post by paddyg on 2005-11-09
as i said, grub doesn't boot windows directly, it just chainloads, in other words the windows loader sort of takes over. If you have one disk you can have one windows loader and one boot.ini. You can have three or four windows partitions but the boot.ini will be one. Windows only installs its loader to the mbr---have you got any other choice?

BTW, what's wrong with the windows boot screen?

---

