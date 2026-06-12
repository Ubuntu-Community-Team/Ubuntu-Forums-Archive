---
title: "EasyBCD can't locate Ubuntu 8.10 GRUB"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by smashdoez on 2008-12-06
(I've searched, but didn't find anything that works for my case)

I have two hard drives, one with Vista and the other for Linux.

Wanting to keep Windows and Linux completely separate, I disconnected my Vista drive during the Ubuntu 8.10 x64 installation. I installed 8.10 on hd0,0 (hd1,0 with the Vista drive attached).

The problem I have is since I didn't create a separate NTFS partition for GRUB, EasyBCD cannot identify my 8.10 installation and therefore will not boot.

My Windows boot data resides on a 200mb partition on Hd0,0 and that is where EasyBCD is looking for the menu.lst

To further complicate matters, the HD I installed Ubuntu on was originally partitioned as GPT.  I thought I had re-formatted and re-converted back to MBR, but as it turns out, it's still GPT.  When the EasyBCD menu.lst uses the:  

find --set-root --ignore-floppies /boot/grub/menu.lst
configfile /boot/grub/menu.lst

It returns unrecognised partition table for drive 80 / error 17:


So how do I make 8.10 bootable?  Can I create a NTFS partition and copy / install the GRUB loader to that partition?  If so, how?  Or am I looking at a fresh format?

Any tips, ideas much appreciated.

---

### Post by caljohnsmith on 2008-12-06
Probably your best bet would be to reformat your Ubuntu drive with a standard MS-DOS partition table (not the current GPT one), and then reinstall Intrepid. You don't have to disconnect your Windows drive when you install Ubuntu, just make sure in the last step of the installation process, click on the "advanced" button, and there you can specify to have Grub installed to /dev/sdb or whichever is your Ubuntu drive. Is there anything on the Ubuntu drive you need to save first? If so, how about opening a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want. :)

---

### Post by smashdoez on 2008-12-06
hi Cal, thanks for the reply.

I decided it would be a lot simpler to CLEAN the disk and remove the GPT properly this time and to start from scratch.

Since it was a new installation with only updates and a few tewaks, I wasn't going to lose anything.  Everything is working fine now :)

Handy tip about the advanced button too :)

---

