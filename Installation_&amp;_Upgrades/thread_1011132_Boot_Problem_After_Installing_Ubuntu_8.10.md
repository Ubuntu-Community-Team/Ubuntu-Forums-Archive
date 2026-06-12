---
title: "Boot Problem After Installing Ubuntu 8.10"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by ulusu on 2008-12-14
Hello. I have a dual boot windows XP - Ubuntu 8.04., and i wanted to install Ubuntu 8.10 to one of my empty partitions. 8.10 was installed with no problem, but it removed other two operating systems from grub menu. Then i formatted ubuntu 8.04 and reinstalled 8.10 on its partition. I added windows entry manually to menu.lst file, but
```
Error 12: Invalid device requested

Press any key to continue..
```
error is occured when selecting windows XP entry from grub at startup. My boot info file is in attachment. 
Thanks for your help.

---

### Post by Herman on 2008-12-14
I think you should hash out or delete the 'makeactive' command in your menu.lst booting stanza for Windows. 
The makeactive command is for setting the boot flag or making sure it is set in the Windows partition. You already have a boot flag in your Windows partition, that's good.
The reason for the error message is that GRUB can't set a boot flag in a logical partition, only in a primary partition. But you already have the boot flag set, so you don't need to do it again. GRUB doesn't seem to know that, so it tries again anyway, but fails with the error message and gets stuck there. If you just get rid of that makeactive command it should start working.

Also, I don't think you need the 'map' commands do you? Those are only needed when you have Windows on a second, third or fourth (...or so on), hard disk. I would get rid of those too, since it looks to me like you only have one hard disk. :)

Regards, Herman :)

---

### Post by caljohnsmith on 2008-12-14
deleted, sorry double post.

---

### Post by caljohnsmith on 2008-12-14
I agree with Herman, I think one of the things you need to do to get XP booting is to remove the "makeactive" and "map" lines in your menu.lst, so I would instead use:
```
title Windows XP Professional
rootnoverify (hd0,4)
chainloader +1
```
Also, your boot.ini file needs to point to the correct partition, so how about doing:
```
sudo mount /dev/sda5 /mnt
gksudo gedit /mnt/boot.ini
```
And change the partition numbers as follows:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)[COLOR="Blue"]partition(1)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)[COLOR="Blue"]partition(1)[/COLOR]\WINDOWS=”Microsoft Windows XP Professional” /fastdetect
```
Save the boot.ini file, and then just to make sure it keeps its DOS style end-of-lines, do:
```
sudo apt-get install tofrodos
sudo unix2dos /mnt/boot.ini
```
After that, reboot, and let us know exactly what happens when you choose XP from the Grub menu. We can work from there if you want.

---

### Post by ulusu on 2008-12-14
Yes, that's it..:p  Modifying my windows entry in grub's menu.lst file as
```
title Windows XP Professional
rootnoverify (hd0,4)
chainloader +1
```
solved my problem.
Thanks lot for your helps.

---

