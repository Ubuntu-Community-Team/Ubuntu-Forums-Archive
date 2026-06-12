---
title: "Error 13 in GRUB"
date: 2008-07-30
forum: General Help
---

### Post by eximius1 on 2008-07-30
Hi,

I'm triple booting Dell Media Driect, Vista and Ubuntu.

I used QGRUB editor to change the names of the OS's to try and make the GRUB screen a little more attractive. But now when I try and load Vista or MD I just get "Error 13: "Invalid or unsupported executable format".

This is my menu.lst file:

```
default 0
timeout 10

title Ubuntu 8.04.1
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=9be5a6ae-93e4-4786-8aef-37aecc7bdbeb ro quiet splash i8042.nomux=1
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1 (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=9be5a6ae-93e4-4786-8aef-37aecc7bdbeb ro single
initrd /boot/initrd.img-2.6.24-19-generic

title memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Windows Vista
root (hd0,6)
chainloader +1
savedefault
makeactive

title Dell Media Direct
root (hd0,6)
chainloader +1
savedefault
makeactive
```

This might help as well:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       96390   188844074    94373842+   7  HPFS/NTFS
/dev/sda3       188844075   625137344   218146635    f  W95 Ext'd (LBA)
/dev/sda5       620928378   625137344     2104483+  dd  Unknown
/dev/sda6       188844201   200555459     5855629+  82  Linux swap / Solaris
/dev/sda7       200555523   249826814    24635646   83  Linux
/dev/sda8       249826878   620928314   185550718+  83  Linux

Partition table entries are not in disk order
```


Any and all help would be appreciated, thanks.

---

### Post by geirha on 2008-07-30
All entries have root (hd0,6), which should be the ubuntu partition. The windows entry should probably have (hd0,1) and the dell thingy (hd0,0)

---

### Post by eximius1 on 2008-07-30
Shouldn't it be MD hd0,1 and vista hd0,2?

Or am I not getting this?

Even then is it a simple matter or changing the menu.lst file?

Thanks by the way.

---

### Post by geirha on 2008-07-30
the device nodes /dev/sda1, /dev/sda2 etc starts counting from 1. Grub's (hd0,0), (hd0,1), etc starts counting from 0, so /dev/sda1 maps to (hd0,0).

You just edit /boot/grub/menu.lst with the proper values, yes.

---

### Post by eximius1 on 2008-07-30
Thanks. Worked perfectly.

---

### Post by geirha on 2008-07-30
I should add that when a new kernel package comes along now, it will not be added to your grub menu. It needs some of the special comments in the original menu.lst that ships with ubuntu in order to add new kernels. I would recommend that you move away your /boot/grub/menu.lst (e.g. **sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup**) Then run ```
sudo update-grub
``` which will create a new menu.lst with all the kernels you have installed, and with the proper comments it needs. Then, copy/paste the windows and dell sections of your previous menu.lst to the end of your new menu.lst ...

Read more about this at [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by eximius1 on 2008-07-30
Thanks again, nice to find such a helpful person, This is why I love Ubuntu :)

---

