---
title: "Remove Linux :("
date: 2005-11-19
forum: General Help
---

### Post by Malcom on 2005-11-19
Hi, i need some help to formate the linux "part of the hdd" to get that OS choose menu away.... i have to reinstall everything on my cpu.. :P
1, i need to remove Linux.
2, i have to reinstall windows.

yeah yeah..got both windows and Linux.. now i need help to get the formate commande for linus ubuntu 5.10 :)

---

### Post by adwait on 2005-11-19
in windows run
```
fdisk /mbr
```

This will get rid of GRUB. Now you can just format the partitions with any partitioning utility.

---

### Post by proxess on 2005-11-19
[QUOTE=Malcom]Hi, i need some help to formate the linux "part of the hdd" to get that OS choose menu away.... i have to reinstall everything on my cpu.. :P
1, i need to remove Linux.
2, i have to reinstall windows.

yeah yeah..got both windows and Linux.. now i need help to get the formate commande for linus ubuntu 5.10 :)[/QUOTE]

let me try to get this right, you want to remove the linux partition ("part of the hdd") and remove the menu (grub?!) from the boot? Without or with formating windows partition?!

Well if you want to do this without removing windows, all you have to do is delete the linux and swap partitions (use a program called 'Partition Magic' for windows), boot the windows xp cd and choose, choose recovery and then 'fixmbr'. This is only available for winXP professional.

If you want to reinstall windows, just grab a windows cd, put it in your cd drive and let it run.


Its a shame to see someone stop using linux.

-Proxess

---

### Post by Malcom on 2005-11-19
well :( the thing is.. i got a new motherboard and a new g-card and a new netshit..
so i cant go into windows... and i cant format.. cuz it wont read my windows xp CD :(
please help me ^^

---

### Post by Cyril on 2005-11-19
Is it possible that boot from CD is not enabled?

Also it is probably not neccessary to reinstall windows.  You can delete the linux partition and resize your ntfs partition.

---

### Post by rcerreto on 2005-11-19
Do you mean you can't boot from WindowsXP CD??
That's pretty weird.
Did you check into BIOS that booting from CD comes before than booting from HDD?

---

### Post by proxess on 2005-11-19
To see your bios, when you start up your pc quickly press DELETE or DEL keys. Then search for a 'BOOT' option. Make sure that 1st boot is on CD drive.

Don't know if you know this or not, so heres how you check anyhow.

---

### Post by ferentix on 2005-11-19
Actually it may not be delete, but it ought to say just after your computer is turned on "hit xxx to enter BIOS" or "press xxx to enter setup" or something along those lines. On one of my computers it's Delete, the other it's Escape... this may be unconventional, I don't know, but then Malcoms may also be that way.

Why are you getting rid of Ubuntu Malcom? :( Just wondering... ;)

---

