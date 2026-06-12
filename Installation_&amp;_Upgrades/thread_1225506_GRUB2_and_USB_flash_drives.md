---
title: "GRUB2 and USB flash drives"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by m-p{3} on 2009-07-28
Hello,

I'm currently trying to build myself a bootable USB thumbdrive from which I could boot a list of ISOs files. I know GRUB2 allow to boot ISOs files without the need of extracting the ISO content and some users made grub.cfg files showing how to do it.

The only thing I'm having issues with is how to get GRUB2 to be the USB thumbdrive MBR. I'm currently doing the test with a Karmic Koala Alpha 3 Live CD, so if someone has a good tutorial on how to do this, I would be very interested.

Thanks a lot!

m-p{3}

---

### Post by Mighty_Joe on 2009-07-29
Grub2 is pretty sparsely documented.  There's this in the [manual]("http://grub.enbug.org/Manual#head-fd9419d355d93aaa8086f8c00dcb44ed2cdac88b"):
> Special Write Targets

    * Write grub to USB drive 

The example command # grub-install --root-directory=~/usbdrive/ /dev/sdb installs to a USB drive enumerated at sdb, and which was also mounted at usbdrive. It was taken from UseCases/Ubuntu. 

I don't know if Grub2 is ready.  The [FAQ]("http://www.gnu.org/software/grub/grub-2-faq.en.html") says it is "usable" but to expect incompatible changes.

---

### Post by m-p{3} on 2009-07-29
Alright, thanks for the information. I'll try to find more details if Google can get something better.

---

### Post by m-p{3} on 2009-07-29
After some testing, it seems I managed to put the GRUB2 on the flashdrive MBR, but I get into the rescue mode. I guess I'm doing something wrong, but I guess I'll figure it out eventually.

I'll keep trying, and once I got an ISO to boot from GRUB2 I'll post some informations. If anybody can assist, I'm open for suggestions.

---

### Post by Mighty_Joe on 2009-07-30
There's a discussion going on [over here]("http://ubuntuforums.org/showthread.php?t=1224417&highlight=grub2") on booting a live CD image with Grub.  Perhaps it, or the linked article, will be useful?

---

### Post by GFRoSTY on 2009-08-04
@ m-p{3}

Can you tell me how you managed to get the GRUB2 MBR onto a USB disk ?

I've tried the grub-setup but only accepts Hd0,hd1 etc

Thanks in advance

---

### Post by Mighty_Joe on 2009-08-06
Have a look at his [other thread]("http://ubuntuforums.org/showthread.php?t=1225506") (and my other post!)

---

### Post by muckblit on 2010-02-07
If usb drive is /dev/sdc and you had sdc1 mounted on /mnt and had /mnt/boot:

sudo grub-install --no-floppy --root-directory=/mnt /dev/sdc

sudo grub-mkconfig -o /mnt/boot/grub/grub.cfg

Then you have to edit that grub.cfg.

This works:

menuentry "Test memory lucid-desktop-i386.iso" {
set quiet=1
insmod ext2
loopback loop (hd0,1)/boot/lucid-desktop-i386.iso
linux16 (loop)/install/mt86plus
}

This boots to initramfs, and grub2's (hd0,1) the usbdrive has become /dev/sdb and there is no /dev/sdb1:

menuentry "Try Ubuntu without installing lucid-desktop-i386.iso" {
set quiet=1
loopback loop (hd0,1)/boot/lucid-desktop-i386.iso
linux (loop)/casper/vmlinuz cdrom-detect/try-usb=true isofrom=/dev/sda1/boot/lucid-desktop-i386.iso root=/dev/ram0 noeject noprompt initrd=(loop)/casper/initrd.lz quiet splash --
initrd (loop)/casper/initrd.lz
}

This has an init script somewhere that has a line 7 that keeps looking for /dev/sr0 mostly and if I remove the usbkey and put it back in, line 7 looks for /dev/sda and /dev/sr0, loop forever:

menuentry "Try Ubuntu without installing lucid-desktop-i386.iso" {
set quiet=1
loopback loop (hd0,1)/boot/lucid-desktop-i386.iso
linux (loop)/casper/vmlinuz cdrom-detect/try-usb=true isofrom=/dev/sda1/boot/lucid-desktop-i386.iso root=/dev/ram0 noeject noprompt file=(loop)/cdrom/preseed/ubuntu.seed boot=casper initrd=(loop)/casper/initrd.lz quiet splash --
initrd (loop)/casper/initrd.lz
}

That init might be in ubuntu.seed or casper scripts.

I also tried easypeasy.

I have a sed script which rips the kernel opts from /isolinux/text.cfg for the lucid and easypeasy iso's. I'm trying the iso loop method because syslinux did not work well on part2, and then grub2 works great with different partitions but beyond part1 the lucid live and easypeasy(karmic) can't find their self usb partition. They're probably changing to /dev/sdb2 from grub2 (hd0,2) /dev/sda2. Guess mapping like for windows might help, and/or fakebios? Also edit the init script wherever that is.

menuentry "Try Easy Peasy without any change to your computer easypeasy-1.5.img.iso" {
set quiet=1
loopback loop (hd0,1)/boot/easypeasy-1.5.img.iso
linux (loop)/casper/vmlinuz cdrom-detect/try-usb=true isofrom=/dev/sda1/boot/easypeasy-1.5.img.iso root=/dev/ram0 noeject noprompt file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
initrd (loop)/casper/initrd.gz
}

---

### Post by darkeyes7777 on 2010-02-08
> **muckblit said:**
> If usb drive is /dev/sdc and you had sdc1 mounted on /mnt and had /mnt/boot:

sudo grub-install --no-floppy --root-directory=/mnt /dev/sdc

sudo grub-mkconfig -o /mnt/boot/grub/grub.cfg

Then you have to edit that grub.cfg.

This works:

menuentry "Test memory lucid-desktop-i386.iso" {
set quiet=1
insmod ext2
loopback loop (hd0,1)/boot/lucid-desktop-i386.iso
linux16 (loop)/install/mt86plus
}

This boots to initramfs, and grub2's (hd0,1) the usbdrive has become /dev/sdb and there is no /dev/sdb1:

menuentry "Try Ubuntu without installing lucid-desktop-i386.iso" {
set quiet=1
loopback loop (hd0,1)/boot/lucid-desktop-i386.iso
linux (loop)/casper/vmlinuz cdrom-detect/try-usb=true isofrom=/dev/sda1/boot/lucid-desktop-i386.iso root=/dev/ram0 noeject noprompt initrd=(loop)/casper/initrd.lz quiet splash --
initrd (loop)/casper/initrd.lz
}

This has an init script somewhere that has a line 7 that keeps looking for /dev/sr0 mostly and if I remove the usbkey and put it back in, line 7 looks for /dev/sda and /dev/sr0, loop forever:

menuentry "Try Ubuntu without installing lucid-desktop-i386.iso" {
set quiet=1
loopback loop (hd0,1)/boot/lucid-desktop-i386.iso
linux (loop)/casper/vmlinuz cdrom-detect/try-usb=true isofrom=/dev/sda1/boot/lucid-desktop-i386.iso root=/dev/ram0 noeject noprompt file=(loop)/cdrom/preseed/ubuntu.seed boot=casper initrd=(loop)/casper/initrd.lz quiet splash --
initrd (loop)/casper/initrd.lz
}

That init might be in ubuntu.seed or casper scripts.

I also tried easypeasy.

I have a sed script which rips the kernel opts from /isolinux/text.cfg for the lucid and easypeasy iso's. I'm trying the iso loop method because syslinux did not work well on part2, and then grub2 works great with different partitions but beyond part1 the lucid live and easypeasy(karmic) can't find their self usb partition. They're probably changing to /dev/sdb2 from grub2 (hd0,2) /dev/sda2. Guess mapping like for windows might help, and/or fakebios? Also edit the init script wherever that is.

menuentry "Try Easy Peasy without any change to your computer easypeasy-1.5.img.iso" {
set quiet=1
loopback loop (hd0,1)/boot/easypeasy-1.5.img.iso
linux (loop)/casper/vmlinuz cdrom-detect/try-usb=true isofrom=/dev/sda1/boot/easypeasy-1.5.img.iso root=/dev/ram0 noeject noprompt file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
initrd (loop)/casper/initrd.gz
}



i have tried to di this but the grub.cfg file generated on usb driver is the same of my  hard disk S.O. grub.cfg!

then if i modify the configuration file on usb stick as i want, in the next reboot grub doesn-t fell the change and load instead the same my hard disk grub.cfg.

---

### Post by darkeyes7777 on 2010-02-08
a little off topic

do anyone know if for syslinux there is a command like grub^s root (hd0,1) to manage wich partition boot??

---

