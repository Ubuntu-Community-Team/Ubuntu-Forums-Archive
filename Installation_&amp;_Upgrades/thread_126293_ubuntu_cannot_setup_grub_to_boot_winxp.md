---
title: "ubuntu cannot setup grub to boot winxp"
date: 2006-02-06
forum: Installation &amp; Upgrades
---

### Post by kakashi on 2006-02-06
i have been using ubuntu for a long time and have never had this problem. i installed windows xp then ubuntu but ubuntu DID NOT detect the winxp partition. this never happened on my old computer so i suspect the harware to be a cause. 
my computer is 
amd opteron 165 (think amd x2 3800+ only higher quality)
DFI infinity nf4 sli
WD ide HDD
ati x800.

i installed winxp 
and the amd64 version of ubuntu. 
i have tried to use a older hoary i386 cd to just install grub but even that only detect the ubuntu partion. i have also tired making the winxp partitions fat32 and ntfs.

---

### Post by kakashi on 2006-02-06
i suppose i forgot to ask for hwlp in my hurry. but thats implied is it not....
please please help. i just bought this aweome computer so i can play games (so don't tewll me to get rid of windows) but i feel so help without a linux command line (especially miss mplayer,mencoder).... i really need to get this working

---

### Post by _Luiz_ on 2006-02-06
Try to edit the menu.lst file in /boot/grub

The WinXP section of my file is this:
Change where is needed (like the partition)

title		Microsoft Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

well, good luck. ;)

---

### Post by kakashi on 2006-02-06
bump

---

### Post by Sutekh on 2006-02-06
[QUOTE=kakashi]i installed windows xp then ubuntu but ubuntu DID NOT detect the winxp partition.[/QUOTE]
f you installed Windows *after* Ubuntu, then Ubuntu needs to be told to look for the WinXP, it won't detect it automatically, because things have changed.

_Luiz_'s advice will probably get you on your way.

If you want more detailed advice, could you supply the output of
```
sudo fdisk -l
```
so we know what your partitions are and where they are, and
```
cat /boot/grub/menu.lst
```
so we know what GRUB thinks about the whole situation and what it's trying to do.

---

### Post by kakashi on 2006-02-17
somebody close this thread plase.
also it seems to work now.

---

### Post by kakashi on 2006-02-17
somebody close this thread plase.
also it seems to work now.

---

