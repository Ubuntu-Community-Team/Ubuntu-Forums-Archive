---
title: "Booting ubuntu iso off of hard drive"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by n0083 on 2009-08-02
[FONT=-moz-fixed]Hello,

The ubuntu installer for the hd-media (9.04) is not recognizing the iso.

I am using:
     Machine:
     EEE PC 1000 HA
     WindowsXP Home SP3
     Intel® Atom N270 1.6 GHz
     1 GB DDR2 RAM
     [http://eeepc.asus.com/global/product1000ha-spec.html](http://eeepc.asus.com/global/product1000ha-spec.html)

I have an NTFS primary partition at hda(0,0) (C: drive), i have a Fat32 partition at hda(0,1) (L: drive).

I changed the windows boot.ini to boot into grub4dos (0.4.4).  I changed one of my menu options to:

title  New Install
kernel (hd0,1)/boot/newinstall/vmlinuz
initrd (hd0,1)/boot/newinstall/initrd.gz

the above two files are located at
L:/boot/newinstall/vmlinuz
L:/boot/newinstall/initrd.gz

I also have iso located at:
L:/ubuntu-9.04-desktop-i386.iso

The grub4dos boot works.  Selecting the 'New Install' menu option seems to load up the two files just fine.  The problem is installers can't seem to read the iso file.  The installer says it found possible isos, but the installer complains that either the cdrom drive (which i don't have) is having issues or the iso is corrupt.

From cygwin when i do 'file ubuntu-9.04-desktop-i386.iso' i get "...ISO 9660 CD-ROM filesystem data UDF filesystem data...."

Any help would be much appreciated.

(no i don't have a thumb drive)

Thanks,
dK
`

-- 
ubuntu-users mailing list
[EMAIL="ubuntu-users@lists.ubuntu.com"]ubuntu-users@lists.ubuntu.com[/EMAIL]
Modify settings or unsubscribe at: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-users](https://lists.ubuntu.com/mailman/listinfo/ubuntu-users)


[/FONT]

---

