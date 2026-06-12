---
title: "Problems booting from USB (now boot without usb is not possible)"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by seppl82 on 2009-03-03
Hi all,

today i've installed Ubuntu on a removable usb stick. For the installation i've used the regular installer.

The problem is now that the usb stick itself does not boot if i select it from the bios and the Windows System on the Harddisc can not boot without the USB Stick. If i start the Notebook without the USB Stick i get the error that GRUB is not working because it does'nt find the necessary files.

Question: Is it possible to restore the windows bootloader and install the grub bootloader on the usb drive?

Kind Regards
Seppl

---

### Post by maybeway36 on 2009-03-03
You can restore the Windows MBR in a few different ways.
In Linux:
```
dd id=/dev/zero of=/dev/xxx bs=440 count=1
``` (if you forget the count=1, it will erase your whole hard drive!)
In DOS:
```
fdisk /mbr
```
With Windows recovery console:
```
fixmbr
```

---

### Post by seppl82 on 2009-03-03
Hey cool,

thanks alot.
How about my second problem. How can i write the bootloader to the usb drive?

Kind Regards
/Seppl

---

### Post by Rallg on 2009-03-03
There are several ways to write the bootloader to the USB drive. I will suggest one:

Consider using "grub4dos" program. It is a bootloader that is completely independent of the bootloader you already have. It does not interfere with your current installation, and does not interfere with ordinary files that you may want to put on the USB.

Start with a blank USB (it does not have to be large). Using Windows (not Ubuntu), search the Internet and find the "HP USB Disk Storage Format Tool" from a reliable source. You may also need to locate a minimal set of DOS system files (these can be extracted from XP with difficulty, but useful files are also circulating here and there on the Internet). With these, you can turn the USB into a bootable device, when you boot it, you get a DOS prompt.

Then, get "grub4DOS" and put it on the USB. The idea is that when you boot to the USB and get the DOS prompt, you call grub4DOS, and get a bootloader that looks like grub. This can also be auto-launched, if you wish.

Then, you would need to edit the menu.lst used by grub4DOS, so that it refers to the systems on your hard drive. Just remember that grub4DOS thinks the USB is hd0, and that your hard drive is hd1. Also remember that this menu.lst will not be auto-updated if you update grub on the hard drive. you have to do it manually. it's easy.

The rest of the space on the USB is an ordinary FAT file system that can store files and be read by Windows or Ubuntu.

---

### Post by seppl82 on 2009-03-04
Hi,

i did the following to make the USB stick bootable (/dev/sdb is my stick)

[FONT="Courier New"]grub-install /dev/sdb[/FONT]

To remove the Grub loader from the physical harddisk i used the following windows tool

[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

Thanks ALOT

/Seppl

---

