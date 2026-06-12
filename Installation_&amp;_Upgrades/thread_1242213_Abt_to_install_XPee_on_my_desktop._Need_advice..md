---
title: "Abt to install XPee on my desktop. Need advice."
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by draperdt on 2009-08-16
Hi,

I have a triple boot setup with Mint 7 KDE, Fedora 11 and Windoze 7. Everything is working fine....not perfect but fine enough since its doing the job.

Now, I have to install XPee so that I can work for a particular project and I was wondering if anyone could advice me on what are different speed bumps I am looking at. 

I dont want my grub to disappear or be broken because I dont have the time and patience to go through all that again :(
 

Current setup:

**First the fdisk. This is what I get from fdiskin it.**

```
 Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbab2bab2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22946   184313713+  83  Linux
/dev/sda2           25497       29650    33367005    7  HPFS/NTFS
/dev/sda3           29651       30401     6032407+   5  Extended
/dev/sda4           22947       25496    20482875   83  Linux
/dev/sda5           29651       30401     6032376   82  Linux swap / Solaris
```  **menu.lst from the grub for Fedora (sda4) is** > title Fedora 11
        root (hd0,3)
        kernel /boot/vmlinuz-2.6.29.4-167.fc11.x86_64 ro root=UUID=6605a68a-e359-4f35-a436-b2b3c65071da
        initrd /boot/initrd-2.6.29.4-167.fc11.x86_64.img

title Mint 7 - Gloria
root (hd0,0)
kernel /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title  Windoze 7
        rootnoverify (hd0,1)
chainloader +1
**Menu.lst from Mint 7 (sda1) is: **
> title           Debian GNU/Linux, kernel 2.6.28-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic

title           Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Debian GNU/Linux, kernel memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin

So, I want to use gparted and create a NTFS partition from sda1 and install XPee. My question, will the grub disappear and if so, I have both the Fedora and Mint dvds handy. 

What do I do after the grub disappears and how do I get it back?

Say, somehow I get the grub back up, Do I chain load it? And if so, can I just say:

```
 title XPEEEE
        rootnoverify (hd0,5)
chainloader +1
``` assuming the new partition will be sda6? :)

Thanks.

---

### Post by draperdt on 2009-08-18
bump?

---

### Post by Mark Phelps on 2009-08-19
You're probably not getting answers because this is the Ubuntu forum, not the Mint or Fedora forums, and while the general answer in Ubuntu would be (1) if you installed GRUB to your MBR, it will get overwritten by XP when you install it, and (2) you fix that by booting from an Ubuntu LiveCD and reinstalling GRUB, the details might be different for Mint or Fedora.

And if you used LILO for those, there may not be folks here familiar enough with LILO to give you the details needed.

I think you might do better checking the Mint and/or Fedora forums for the details.

Also realize that if you install Window 7 after XP, the Windows 7 boot loader finds XP and adds it to the MS Windows boot menu -- but the reverse does not happen.

So, after you've done this, depending on how you go about selecting your OS at boot time, you might have considerable work ahead to be able to boot to either XP or Windows 7.

---

