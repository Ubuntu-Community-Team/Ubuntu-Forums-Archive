---
title: "[SOLVED] re writing Grub"
date: 2008-07-29
forum: General Help
---

### Post by tropdoug on 2008-07-29
Hi guys, 

I stuffed it again! I have (very reluctantly) had to reinstall WinXP for my partner who MUST use MS Office for a course she is undertaking. So using Gparted I shrank the root partition to give me another partition space and prepared it for ntfs. 

After doing the install, I went to restart and of course nothing happened. I used the live cd, and checked that all folders, directory structure on the root partition were unharmed and they are all there, seem normal. I looked at the Grub menu.lst and no windows items yet. 

Obviously I have to re write grub to the boot sector, how can I do that, and how would I include the XP item so I can dual boot. Or do I have to reinstall the system. (I am still using gutsy at this time, and don't want to upgrade yet) 

Thanks for any help

Douglas
</div>

---

### Post by DagMan on 2008-07-29
You want to run a live cd, open a terminal, and find out which partition is the one with the /boot folder on it.  Unless you put /boot on its own partition, it will be in the same partition as /
and if you installed just / and swap partitions then that makes it even easier.  If you don't already know which one it is, have a look at the partition table
```
sudo fdisk -l
```

lets say for argument that your root partition is at /dev/sda2
this is the first hard drive and first partition.  Grub, however starts counting from 0 and not 1 and uses numbers, starting from 0 for the drive number instead of letters.  /dev/sda1 is (hd0,0) and /dev/sdb2 is (hd1,1) and /dev/sdb3 is (hd1,2)... /dev/sda2 would be (hd0,1)  if this part makes sense then figure out what your / partition (or /boot in the special circumstance that you made it a separate partition which most likely you didn't)

in the example, root is /dev/sda2
type 
```
sudo grub
```
you will get the command promt for grub, you arent in bash any longer, for the time being.
type 
```
root (hd0,1)
```
this tells grub that your boot directory (root partition in most cases) is at the first hard drive and second partition, /dev/sda2 (again, grub counts from 0 and upwards, not 1)
then to write it to your mbr type where you want to install it to.  The mbr for the first hard disk is just (hd0)
```
setup (hd0)
```
if you did it okay, it shouldn't give you an error but give you some positive looking jibber jabber, and not "error"
to leave the grub prompt.
```
quit
```
Then hopefully you can reboot and select ubuntu.

Once you are in ubuntu you will have to edit the file /boot/grub/menu.lst to add the entry for Windows.
```
sudo gedit /boot/grub/menu.lst
```
at the very bottom of the file where it has the options for ubuntu and memtest, add one for windows
```
title		Windows 
root		(hd0,0)
makeactive
chainloader	+1

```
You see above that in the line that says 'root' there is the grub notation again (hd0,0) in this example it means the first hard drive and first partition or /dev/sda1. If yours is differant, change it accordingly  The other thing that may need to change is that somtimes the line that says 'root' needs to say 'rootnoverify' instead. You probably won't need that for most setups, but if you do, you know where the file is to edit it.

---

### Post by Krupski on 2008-07-29
> **tropdoug said:**
> Obviously I have to re write grub to the boot sector, how can I do that, and how would I include the XP item so I can dual boot. Or do I have to reinstall the system. (I am still using gutsy at this time, and don't want to upgrade yet) 


OK... to add an entry to 'menu.lst' which will allow booting Windows, add the following to 'menu.lst':

[COLOR="Red"]**_NOTE - READ CAREFULLY FIRST - DO NOT SIMPLY CUT-N-PASTE THIS CODE!!!_**[/COLOR]

```

title         Windows XP
root          (hd0,0) [COLOR="Red"]**<-- note whatever drive it's on**[/COLOR]
makeactive
chainloader   +1

```

To put grub ONTO a drive, do this:

```

grub-install /dev/sda [COLOR="Red"]**<-- note whatever drive it's on**[/COLOR]

```

Whatever drive you want to be the default (i.e. the one that boots up if you don't do anything), simply make it first in the list.

Of course, you must use 'sudo' or be root to do this...

Good luck


-- Roger

---

### Post by tropdoug on 2008-07-29
Thank you both for such quick replies. I have gone through the process, and bingo all is running normally again. Thanks very much, just shows that even when a novice makes a mess, its usually fixable, unlike the "other" system.

I have another question, but it's a new subject so I will make new post in case other newer people may have the same issue. Once again Thanks. 

Douglas

---

