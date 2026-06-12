---
title: "[SOLVED] Move GRUB to Ubuntu Disk"
date: 2008-10-05
forum: General Help
---

### Post by ks07 on 2008-10-05
Hi guys,

I don't know why, but my first HDD has crapped out (again). I can't boot into Ubuntu or Windows because GRUB was installed to the default location, which I'm pretty sure is the MBR of the first hard drive. I need someone to tell me how I can move GRUB to the MBR of the second hard drive where Ubuntu is installed. Once that is done will I be able to swap the boot order of the disks and boot from the second drive? I'm running from the Live CD atm.

Output of fdisk -l:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b485a

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        4863    39062016   83  Linux
/dev/sde2            4864       19457   117226305    5  Extended
/dev/sde5            4864       15319    83987788+  83  Linux
/dev/sde6           15320       18971    29334658+   b  W95 FAT32
/dev/sde7           18972       19457     3903763+  82  Linux swap / Solaris

sde1=/
sde5=home
sde6=shared
```

---

### Post by caljohnsmith on 2008-10-05
Try these steps from a terminal in the Live CD in order to install Grub to the MBR of your working Ubuntu drive:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how it goes or if you run into problems.

---

### Post by ks07 on 2008-10-06
Followed your instructions, rebooted without Live CD and got to the GRUB page. It still showed Windows options at the bottom but I selected Ubuntu anyway.

It gave me a 'disk not found' error, or very similar. I just tried running update grub but got the following output:
```
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

ubuntu@ubuntu:~$ 

```

EDIT: Do I need to edit the menu.lst file manually?

---

### Post by caljohnsmith on 2008-10-06
OK, go ahead a reboot again, and when you get the Grub menu, select Ubuntu, hit "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,0)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to:
```
#groot=(hd0,0)
```
Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by bgiannes on 2008-10-06
2 cents..

super grub at [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)  can help...

---

### Post by ks07 on 2008-10-06
> **bgiannes said:**
> 2 cents..

super grub at [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)  can help...
Ty for the link, I'll look into that if I have any more trouble/ 

> **caljohnsmith said:**
> OK, go ahead a reboot again, and when you get the Grub menu, select Ubuntu, hit "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,0)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.


So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to:
```
#groot=(hd0,0)
```
Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

Thanks a billion mate, Ubuntu boots fine now. :guitar:

---

### Post by caljohnsmith on 2008-10-06
That's great news, and glad I could help out. Cheers and have fun. :)

---

