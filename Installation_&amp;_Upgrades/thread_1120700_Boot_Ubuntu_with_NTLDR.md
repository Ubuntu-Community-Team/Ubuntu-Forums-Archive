---
title: "Boot Ubuntu with NTLDR"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by camper365 on 2009-04-09
I installed Ubuntu, and took the whole disk up. However, before this, I made a backup of my Windows partition, and I decided that I needed Windows back. So I copied the files back.
GRUB wouldn't let me boot Windows (it gave me an Error 12: Requested Device Not Found). However, I booted up the Windows Recovery Console, and selected fixmbr. Now I can boot Windows, but I can't boot Linux without going onto the LiveCD in Ubuntu and installing GRUB. At that point, I can't select Windows to boot.
However, I can use NTLDR.
How do I get NTLDR to boot Windows, and go to the GRUB menu if I select it.

---

### Post by ronparent on 2009-04-09
I don't thinkit can be done like that? You probably use a tird party boot loader that would work with your version of windows. You should, however, be able to reinstall the grub boot loader configured to boot both. If that were your choice you can do it as follows:

Booting to the ubuntu live cd start a terminal. Enter commands as follows -

sudo grub

## find you ubuntu install in grub notation with next command

grub> find /boot/grub/stage1

## use this notation to set your root for Ubuntu

grub> root (hd?,?) ## seting the root as the locatin found above

grub> setup (hd0)

This last command should restore a dual boot. You can verify it by rebooting.

---

### Post by dandnsmith on 2009-04-09
It is possible - the PC I am sitting at right now does it that way.

What you have to do is go through the GRUB install, preferably not to the MBR, grab the first sector of the partition in which you have installed it by something like:

dd if=/dev/hda1 bs=512 count=1 of=grubboot.lin (but get the path right)

Copy the grubboot.lin to the partition which Windows is booting from, and make an additional entry in the boot.ini something like:

C:\grubboot.lin="Linux GRUB menu"

---

