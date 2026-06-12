---
title: "Help to set a bootloader (GRUB2) URGH"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by yermandu on 2009-10-24
I always use grub 0.97. And when i want use or test new distro, im add the entries manually.
I dont install another grub.

But this time, im trying use :confused:  grub2 :confused: 

First, i try install grub2 in my boot partition the 
/dev/sda2 

In sometime of the installation i INSTALL GRUB2 IN MBR 

The issue starts, i can boot only UBUNTU, and not my other distros ....


=======================
[http://pastebin.ubuntu.com/300721/](http://pastebin.ubuntu.com/300721/)



I Want make some thing like

Ubuntu 
Ubuntu Rescue
Testmem
Load Grub1

Can i use chainloader? If yes how? How i can load from Grub2(grub.cfg) to grub1(menu.lst)??
Or then, how i can set correctly to load another distros???
I Receive the Error "you need load kernel linux first"

IM using Karmic, 9.10. UbuntuStudio :guitar:

ls /dev/sda2
```
boot@
boot.backup.sda
boot.cat
bzImage-kernel-2.6.31.5-0.rc1.2.1yermandu
clfs.kernel-2.6.31.1
config@
config-2.6.31.4-1.rt14.1mdv
config-2.6.31.5-desktop-0.rc1.1mnb
diag1.img
dicas
gfxmenu*
grub/
initramfs-genkernel-x86-2.6.30-gentoo-r6
initrd-2.6.31.4-1.rt14.1mdv.img
initrd-2.6.31.5-0.rc1.2.1yermandu
initrd-2.6.31.5-desktop-0.rc1.1mnb.img
initrd-desktop.img@
initrd.img@
initrd.img.old
kernel-2.6.30-gentoo-r6
kernel-genkernel-x86-2.6.30-gentoo-r6
kernel.h@
kernel.h-2.6.31.4-1.rt14.1mdv
kernel.h-2.6.31.5-0.rc1.2.1yermandu
kernel.h-2.6.31.5-desktop-0.rc1.1mnb
lfs-info.files
lost+found/
symvers-2.6.31.5-desktop-0.rc1.1mnb.gz
System.map@
System.map-2.6.31.4-1.rt14.1mdv
System.map-2.6.31.5-0.rc1.2.1yermandu
System.map-2.6.31.5-desktop-0.rc1.1mnb
vmlinuz@
vmlinuz-2.6.31.4-1.rt14.1mdv
vmlinuz-2.6.31.5-0.rc1.2.1yermandu*
vmlinuz-2.6.31.5-desktop-0.rc1.1mnb
vmlinuz-desktop@
```*The vmlinuz of the ubuntu is in /dev/sda6*

Tnx,

---

### Post by Rocket2DMn on 2009-10-24
There is a lot of help available now in the community docs for [Grub2]("https://help.ubuntu.com/community/Grub2"), written by a forum member.  He also has a couple of guides here for getting started with Grub2 -
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

While I haven't fiddled with Grub2 myself yet, one of the biggest differences is that you're not supposed to edit grub.cfg (formally menu.lst) directly.

---

### Post by yermandu on 2009-10-24
:popcorn: 

I reinstall grub 0.97

Reinstall ubuntu studio

Finish without any bootloader

Reboot

Edit my menu.lst

Add 
Title Ubuntu Studio
kernel (hd0,5)/vmlinuz root=/dev/sda6


I am happy with Grub 0.97.

---

