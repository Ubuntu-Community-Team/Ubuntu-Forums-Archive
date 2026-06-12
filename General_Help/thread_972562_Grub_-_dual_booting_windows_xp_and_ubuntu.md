---
title: "Grub - dual booting windows xp and ubuntu"
date: 2008-11-05
forum: General Help
---

### Post by lionheartxxi on 2008-11-05
hi guys i just installed windows xp and reinstalled grub on ubuntu, i have edited the grub script to look like this for windows 

### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2

title Windows XP Professional
root (hd0,1)
makeactive
chainloader +1 
savedefault

_____________________________
HERE IS THE DISK 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14687   117973296   83  Linux
/dev/sda2   *       14688       19173    36033795    7  HPFS/NTFS
/dev/sda3           19174       19929     6072570    5  Extended
/dev/sda5           19174       19929     6072538+  82  Linux swap / Solaris

sda2 is windows.

When i boot up i can see windows xp professional but when i go to it, it just brings up ubuntu. My ubuntu partitions are under (hd0,0).

---

### Post by lionheartxxi on 2008-11-06
This is doing my head in, i hate windows but i need it for gaming.

---

### Post by lionheartxxi on 2008-11-06
Please can someone help me.  Everything is up and running for both ubuntu and windows, alls i need now is for grub to boot windows.  All the tutorials dont work.

---

### Post by pastalavista on 2008-11-06
please post the entire menu.lst so we can see what it has to say about Ubuntu also

---

### Post by lionheartxxi on 2008-11-06
title		Ubuntu 8.04.1, kernel 2.6.24-21-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-server root=UUID=afc5e94c-0bc3-4cae-ade6-3c094d1580b6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-server root=UUID=afc5e94c-0bc3-4cae-ade6-3c094d1580b6 ro single
initrd		/boot/initrd.img-2.6.24-21-server

title		Ubuntu 8.04.1, kernel 2.6.24-19-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=afc5e94c-0bc3-4cae-ade6-3c094d1580b6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=afc5e94c-0bc3-4cae-ade6-3c094d1580b6 ro single
initrd		/boot/initrd.img-2.6.24-19-server

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2

 title Windows XP
	        rootnoverify (hd0,1)
	        root (hd0,1)
	        makeactive
	        chainloader +1

---

### Post by lionheartxxi on 2008-11-06
i installed super grub on the windows partition and it ran at boot and put the mbr script in correctly, look at what i was missing ffs lol. It was the rootnoverify (hd0,1).  I hope this helps other ppl because it is extremely frustrating and loads of different tutorials for it.  

Now i can play counter strike source whooo hoooo.  Ubuntu ftw!!!

---

### Post by lionheartxxi on 2008-11-06
see the thrid and fourth ubuntu entries on the list menu can i delete them because they look like duplicates?

---

### Post by joe180 on 2008-11-06
Hi

I have same setup as you, here is a snippet from my menu.lst

title           Windows 
root            (hd0,1)
savedefault
makeactive
chainloader     +1

If still does not work try restting your MBR from windows the run grub back in ubuntu.

You may have to boot from a live CD / DVD once you have reset your MBR.

Hope this helps

---

### Post by lionheartxxi on 2008-11-06
It did work mate :D, tho i used super grub, not as glamourous as your manually set up.  Thanks for your reply m8

---

### Post by pastalavista on 2008-11-06
The Windows entry isn't the same as your first post. Why does it have the "rootnoverify (hd0,1)" line? How did you edit it? It also lacks the "savedefault" line.

---

### Post by lionheartxxi on 2008-11-06
super grub exe from windows fixed it :D

---

### Post by lionheartxxi on 2008-11-06
Thanks for all your replies. Really appreciate the help!!!

---

### Post by joe180 on 2008-11-06
It means:

> Similar to root (see root), but don't attempt to mount the partition. This is useful for when an OS is outside of the area of the disk that GRUB can read, but setting the correct root device is still desired. Note that the items mentioned in root above which derived from attempting the mount will not work correctly. 

---

### Post by lionheartxxi on 2008-11-06
Wins seems to be fine, drivers an all working fine.  Im on ubuntu atm tho.  Where did you get that article m8

---

### Post by lionheartxxi on 2008-11-06
so it doesnt actually install anything into the mbr and once i uninstall it from windows, it wont boot anymore.  Surely though its the POST that matter and it seems to be doing fine.  hopefully.

---

