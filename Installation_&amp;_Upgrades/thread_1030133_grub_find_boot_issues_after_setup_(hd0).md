---
title: "grub find boot issues after setup (hd0)"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by hgu on 2009-01-04
Hi,

I have tried a lot of different things now to make this work, but have not found anything that works. I have a system with a ubuntu 7.04 on sda1 and a ubuntu 8.10 on sda4 (only one disk in system). I did the ubuntu 8.10 install with the defaults but I did a manual partition to put root in sda4 (that already existed). The install went OK, but I wanted to have the system as before with booting from sda1. So that I could setup 8.10 and mythtv on sda4 when I had time later, this is my mythtv machine. So I went into grub and did

root (hd0,0)
setup (hd0)

to make sure that the system use the /boot/grub on sda1 (did this when system was booted into sda4 (hd0,3)). So now it boots like before into sda1 and ubuntu 7.04.

I edited the /boot/grub/menu.lst on sda1 to include the new 8.10 partition at the end. I expected that would be it to be able to alternatively boot into 8.10.

This is what I added to menu.lst
title           Ubuntu 8.10, kernel 2.6.27-9-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=2e518371-3b60-484e-bbcc-786777e97c53 ro quiet splash 
initrd          /boot/initrd.img-2.6.27-9-generic
boot

I have tried variants without root and uuid instead and without boot in the end. Anyway what it say is that it can't find the file when trying to boot from this ubuntu 8.10. When I enter grub command line at boot (booting from hd), change root to (hd0,3) and do find / it can't find anything. From hd(0,0) it has no problem finding /boot etc. Restarted from ubuntu install live cd (8.10) now the when entering grub (after boot) it is possible for grub to find /boot etc on sda4 (hd0,3).

I know one way around this is to start over and have the menu.lst on sda4 default boot into the sda1 partition, but wanted something more robust since I might reinstall the sda4 partition etc.

Any tip on how to make the alternative boot into 8.10 work?

---

### Post by Herman on 2009-01-04
```
root (hd0,3)
```
```
setup (hd0,3)
```
First, I recommend you install ubuntu 8.10's GRUB on sda4 to the boot sector, the fisrt sector of (hd0,3), so that you will be able to chainload 8.10's GRUB.

This is how to change your menu.lst
```
title           Ubuntu 8.10, chainloader
chainloader        (hd0,3) +1
boot

```
or,
```
title           Ubuntu 8.10, chainloader
root            (hd0,3)
 chainloader  +1
 boot
 
```

---

### Post by hgu on 2009-01-04
Thanks Herman! It now works as I want, the second version with separate root works. The other one had problems.

---

### Post by Herman on 2009-01-04
:D Okay, thanks for the feedback, 
Regards, Herman :)

---

