---
title: "(initramfs)"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by mattius-maximus on 2009-02-06
Installation succeeded i think. But once xubuntu has booted, it stays in (initramfs) command. The message before it says:

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)_

I am not a very bright person when it comes to computers and i decided to try ubuntu after all my friends saying how great it is. any help would be appreciated. thanks

---

### Post by 73ckn797 on 2009-02-06
Try booting from the Live CD. If you can then open Places/My Computer

Select the drive where Ubuntu is loaded. At the top of the directory window, just above the window, if it shows the path info (you may need to click on the document looking icon so that it will display the actual path) the take note of that info. Example: /media/disk-1/, Then go to boot/grub (/media/disk-1/boot/grub) and select and open "menu.lst".

Go to the bottom of the file and look for info which will be similar to the following:
```
## ## End Default Options ##

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=33b41abc-de92-4925-aeb3-815844a1cf66 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic (recovery mode)
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=33b41abc-de92-4925-aeb3-815844a1cf66 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 32bit 8.10, memtest86+
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems: Intrepid Ibez 64bit & MS Windows XP
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 64bit 8.10, kernel 2.6.27-11-generic (on /dev/sdb1)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=55b390fb-cc36-4d8b-91c6-fc1ac0af0766 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
savedefault
```Copy and post that info in a reply.

Go to the Applications/Accessories/Terminal. Then enter the following command:

```
sudo fdisk -l
```Post that info also.

We can work from there.

---

### Post by mattius-maximus on 2009-02-06
Same problem booting from LiveCD... im stuck...

[    0.564031] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Loading please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)_

any command i can use to pass this?

---

### Post by mattius-maximus on 2009-02-06
would it just be easier if i re-installed it in windows? instead of a full install?

---

### Post by 73ckn797 on 2009-02-06
Did you download the image from Ubuntu? Did you do a md5sum check on the file and have you tested the disk itself (only if you can get the the Live CD menu)?

---

### Post by mattius-maximus on 2009-02-06
i ran the installer again. I finally got past that page so it fixed that problem. but now a new problem has arisen lol.

Now once Ubuntu starts up, its shutting the monitor down. wtf?

---

### Post by mattius-maximus on 2009-02-06
now the moniter says 

over size
recommand mode
1280x1024

and then about 3 seconds later, shuts down

---

### Post by mattius-maximus on 2009-02-06
ok i figured it out. i just had to run in safe mode. its fuzzy but once im done running the installer i should be able to adjust the display settings. thanks

---

### Post by 73ckn797 on 2009-02-07
Once you can get up and running, if the resolution is not good then check for restricted drivers via System/Administration/Hardware Drivers. Use what is recommended first.

---

### Post by MartinHansell on 2009-02-08
Hi,

I recently upgraded using the standard online  package manager, but for some reason it was only a partial upgrade... (maybe not all files available?).  Anyhow, I got the same problem... only worse.  My root is not recognized at all.

I since reinstalled 8.10 from the Oct 2008 ISO but I cannot get up and running again.  I did what you suggested and below are my details...

Hope you can point me in the right direction...
Many thanks
Martin
oh, I also did a full search on my system to see where Grub was installed and found a historical mess on my various disks... if you want to see that I can post that also.

```

INSTRUCTION #1 : menu.1st file snippet

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f0766a9e-b3ac-4c0b-bed1-6505602aa9d5
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/Mango-root ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f0766a9e-b3ac-4c0b-bed1-6505602aa9d5
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/Mango-root ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f0766a9e-b3ac-4c0b-bed1-6505602aa9d5
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

INSTRUCTION #2 : ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2ce541e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006cbbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244198583+  8e  Linux LVM

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00bd00bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          30      240943+  83  Linux
/dev/sdc2              31        9729    77907217+   5  Extended
/dev/sdc5   *          31        9729    77907186   8e  Linux LVM

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02830282

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$ 


```



> **73ckn797 said:**
> Try booting from the Live CD. If you can then open Places/My Computer

Select the drive where Ubuntu is loaded. At the top of the directory window, just above the window, if it shows the path info (you may need to click on the document looking icon so that it will display the actual path) the take note of that info. Example: /media/disk-1/, Then go to boot/grub (/media/disk-1/boot/grub) and select and open "menu.lst".

Go to the bottom of the file and look for info which will be similar to the following:
```
## ## End Default Options ##

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic

kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems: Intrepid Ibez 64bit & MS Windows XP
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 64bit 8.10, kernel 2.6.27-11-generic (on /dev/sdb1)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=55b390fb-cc36-4d8b-91c6-fc1ac0af0766 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
savedefault
```Copy and post that info in a reply.

Go to the Applications/Accessories/Terminal. Then enter the following command:

```
sudo fdisk -l
```Post that info also.

We can work from there.

---

### Post by dangden on 2010-02-18
How did you get past the problem? im stuck at this part too...

heres the read out:

Loading, Please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_


i let my computer sit like that for over 20 min

would appreciate the help!

---

