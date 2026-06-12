---
title: "Grub error 17"
date: 2008-08-31
forum: General Help
---

### Post by DSGC on 2008-08-31
First of all I'd like to say that I know there are lots of posts about this error but nothing seems to work for me.

Everything started when I tried to boot Windows the other day. The thing is my computer has a partition that contains the necessary files for restoring the system in case something fails. So instead of selecting the correct Windows partition in the Grub menu I selected this one and when I realized where I was I turned the PC off and that's when the problems started. 

Since that moment every time I turn the computer on I get a message saying "GRUB Loading stage 1.5 Loading, please wait... Error 17" so I couldn't even enter the Grub menu.

I've used the recovery disk for Windows and it lets me access Windows. But when I use the Ubuntu disk I can only access the Live CD mode, it won't let me enter the system in the Hard Disk. The same thing happens when I use the Super Grub Disk. I can enter Windows but not Ubuntu. However with the Super Grub Disk I don't only get the error, but an explanation too. It says that the fileformat could not be recognized. So I guess that's the problem.

This is what the last part of menu.lst looks like
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f27a26df-21ab-4796-a3ac-f5254553136f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f27a26df-21ab-4796-a3ac-f5254553136f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f27a26df-21ab-4796-a3ac-f5254553136f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f27a26df-21ab-4796-a3ac-f5254553136f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

And this is what I get for sudo fdisk -lu in Terminal

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x399c399c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   108776114    54388026    7  HPFS/NTFS
/dev/sda2   *   108776115   215560169    53392027+  83  Linux
/dev/sda3       215560170   220202954     2321392+   5  Extended
/dev/sda4       220202955   234436544     7116795    c  W95 FAT32 (LBA)
/dev/sda5       215560233   220202954     2321361   82  Linux swap / Solaris

```

I hope someone can help me. Thank you

---

### Post by caljohnsmith on 2008-08-31
It looks like your HDD's partition table might have been changed; if everything was booting OK before, your Grub entries for Ubuntu are (hd0,2), which is sda3; but according to fdisk, sda3 is now your extended partition. Your Ubuntu partition now appears to be sda2, which is (hd0,1) for Grub. Is sda4 your Windows recovery partition? I highly suspect that at least according to the partition table, that was moved, because it is highly unlikely you would have manually moved your recovery partition to a logical partition when you installed Ubuntu. 

Where did you get that menu.lst you posted? Is that an old one, or were you able to mount the Ubuntu partition (sda2) and access it OK?

---

### Post by DSGC on 2008-09-01
Actually, I didn't create the recovery partition. The Hard Drive came with a partition for Windows and the other for the recovery files. About a year later I installed Ubuntu in the PC and I created the other two. I haven't changed anything.

I got the menu.lst from /boot/grub in the Ubuntu partition. I accessed it with the Live CD.

---

### Post by caljohnsmith on 2008-09-01
OK, boot up your Live CD again, open a terminal, and do the following:
```
sudo fsck /dev/sda2
```
If it returns any errors and asks if you want to correct them (and let me know if it does), say yes. Then do the following:
```
sudo grub
grub> find /boot/grub/stage2
[COLOR="Blue"][should return your Ubuntu partition as (hd0,1), if it does proceed:][/COLOR]
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
If the above is successful, then edit your menu.lst:
```
sudo mount /dev/sda2 /mnt
gksudo gedit /mnt/boot/grub/menu.lst &
```
And change all the Ubuntu entries to use (hd0,1) instead of (hd0,2). Save, reboot, and let me know how it goes or if you get any Grub errors still. :)

---

### Post by DSGC on 2008-09-01
Wow! It works great now! Thank you so much!

Just one more question. Days ago I tried to modify menu.lst with the built in text editor but it said I didn't have permission to do it. The thing is I only have one account so it should have all permissions, shouldn't it? I know I shouldn't touch things if I don't know what I'm doing, but it's already told me the same thing when I was doing pretty basic stuff.

P.S: Thank you! (again)

---

### Post by caljohnsmith on 2008-09-01
> **DSGC said:**
> Wow! It works great now! Thank you so much!

Just one more question. Days ago I tried to modify menu.lst with the built in text editor but it said I didn't have permission to do it. The thing is I only have one account so it should have all permissions, shouldn't it? I know I shouldn't touch things if I don't know what I'm doing, but it's already told me the same thing when I was doing pretty basic stuff.

P.S: Thank you! (again)
You're welcome, I'm glad your computer is happy and healthy again. :) About the permissions stuff, when you try and modify core system files like menu.lst, you usually have to use "sudo" or "gksudo" to open them as the root user (the root user has privileges to do anything), and then you can modify them. Use "sudo" if you want to run a terminal command as root, and use "gksudo" when you want to open a GUI program as root.

---

### Post by DSGC on 2008-09-01
OK. Thanks! I figure this is pretty basic stuff, but I guess I have to learn gradually ;)

---

