---
title: "Installed Windows, now nothing boots up! ARGH!"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by VitaminBB on 2008-12-13
Ok, so I was sick of trying to get my ipod to play nice with ubuntu and decided to make a windows partition to handle that (and maybe photoshop).

So using Gparted livecd I created a 10gig partition, then formatted it with FAT32 (couldnt select NTFS for some reason).

Then using TinyXP I installed a bare windows os on the 10gig partition, everything is fine and dandy up to this point.

Now when I restart I just see a blinking cursor in the top left corner and nothing else.
[B]
Ideas? Did I pooch my master boot record? if so then simply reinstalling a linux MBR handler should recognize the windows partition and the ubuntu partition no? 
[/B]
BTW this is the first post that ive graduated myself from Absolute Beginner status to Hopeless Noob status, thanks for the help since I first started posting!

---

### Post by Pumalite on 2008-12-13
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by VitaminBB on 2008-12-13
> **Pumalite said:**
> Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Did that and now I am typing this from my regular Ubuntu install, the new problem is when I load up I have no option to chose the Windows OS ...

How can I get GRUB to recognize the Windows install ?

---

### Post by Ifaistos on 2008-12-13
I was under the impression that when you want to have a dual boot machine with windows, you have to first install Windows and then Linux.  Not the other way around.  Windows are a bit particular with that.

I hope I am mistaken, because if I am not... you will not like what you will have to do...

---

### Post by 1467 on 2008-12-13
```
gedit /boot/grub/menu.lst
```

look at the bottom for your windows install it will start some thing like this 

title		window xp
uuid		f91768df-de12-4ae9-9c43-fd0bae72d430
kernel

---

### Post by 1467 on 2008-12-13
> **Ifaistos said:**
> I was under the impression that when you want to have a dual boot machine with windows, you have to first install Windows and then Linux.  Not the other way around.  Windows are a bit particular with that.

I hope I am mistaken, because if I am not... you will not like what you will have to do...


you can do it that way but if u install linux before windows u gust have to add the windows uuid to your menu.lst file

---

### Post by VitaminBB on 2008-12-13
> **1467 said:**
> ```
gedit /boot/grub/menu.lst
```

look at the bottom for your windows install it will start some thing like this 

title		window xp
uuid		f91768df-de12-4ae9-9c43-fd0bae72d430
kernel

What am I supposed to do with that once I find out what it says?

---

### Post by 1467 on 2008-12-13
post it  gust the windows part 

then open your fstab to get your uuid for that partition with this command 
```
gedit /etc/fstab
``` 

then post what fstab says

---

### Post by 1467 on 2008-12-13
if you cant find windows in menu.lst do not worry about it sip it we will gust make a new one

---

### Post by VitaminBB on 2008-12-13
> **1467 said:**
> post it  gust the windows part 

then open your fstab to get your uuid for that partition with this command 
```
gedit /etc/fstab
``` 

then post what fstab says

Here is the only part not # pounded out ...
> 
title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a ro splash vga=799 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-8-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a ro splash vga=799 
initrd		/boot/initrd.img-2.6.27-8-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a ro  single
initrd		/boot/initrd.img-2.6.27-8-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a ro splash vga=799 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a ro splash vga=799 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet



And heres the whole result from fstab ...
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=1e014f50-b550-4614-b6da-bafc7f547599 /home           ext3    relatime        0       2
# /dev/sda2
UUID=e4de8bdf-1e20-4899-bbf3-0b0ddda3759f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by 1467 on 2008-12-13
well i do not c a windows partition in fstab 

give me a min or 2 i have to check some thing fist

---

### Post by 1467 on 2008-12-13
ok sry for the wait 

can you try ```
df
```

and post the out put

---

### Post by 1467 on 2008-12-13
ok try this 

add this to your menu.lst file 


```

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

```

and restart your computer
this will add windows to grub

---

### Post by albinootje on 2008-12-13
Can you post the output from : sudo fdisk -l /dev/sda ?

---

### Post by VitaminBB on 2008-12-13
> **1467 said:**
> ok try this 

add this to your menu.lst file 


```

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

```

and restart your computer
this will add windows to grub

Tried that, when I restart and select Windows it gives an error

---

### Post by VitaminBB on 2008-12-13
> **albinootje said:**
> Can you post the output from : sudo fdisk -l /dev/sda ?

Here it is ...
> 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2490    20000893+  83  Linux
/dev/sda2            2491        2794     2441880   82  Linux swap / Solaris
/dev/sda3   *        2795        4068    10233405    b  W95 FAT32
/dev/sda4            4069       14593    84542062+  83  Linux

---

### Post by albinootje on 2008-12-13
Okay, then try adding at the bottom of the grub config-file :

title         MS-Windows
root          (hd0,2)
makeactive
chainloader   +1

And reboot.

---

### Post by Pumalite on 2008-12-13
Add to your menu.lst; at the bottom:
title  Windows
root  (hd0,2)
savedefault
chainloader +1

---

### Post by VitaminBB on 2008-12-13
Wow, I FINALLY got everything working!!!

Thanks everyone, took some elbow grease on my brain and help from you but all looks setup just great now.

---

