---
title: "Problem with GRUB"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by burn3t on 2007-10-18
Ok well I'm rather new to Ubuntu, I installed the 7.10 version just like ten minutes ago but, GRUB wont load. It says it can't load because of error #21.
[quote=http://www.uruk.org/orig-grub/errors.html]21 : "Unknown boot failure"
This error is returned if the boot attempt did not succeed for reasons which are unknown.[/quote]
I have a JMicron device loader/bios stuff or whatever it is, I read from somewhere (can't remember where) that GRUB doesn't support JMicron or something... Is there any way I can run GRUB or does anyone got a guide on how to install LILO for example instead of GRUB? :\
The same error appeared on (K)Ubuntu 6.10, 7.04 and on this new version.
> Intel C2D E6600
GF 8600 GTS
MSI P965 Neo-F
250Gb IDE HDD

[quote=sudo fdisk -l]
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e1cebd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29645   238123431   83  Linux
/dev/sda2           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris
[/quote]

[quote=menu.lst]
default		0
timeout		3
hiddenmenu

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=60b28e49-b64a-4e1d-84a1-0172c71b412d ro quiet splash locale=fi_FI
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=60b28e49-b64a-4e1d-84a1-0172c71b412d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet[/quote]

[quote=fstab]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=60b28e49-b64a-4e1d-84a1-0172c71b412d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d813f6c1-9941-93d2-7091-8e9b2243506b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0[/quote]

---

### Post by TGArcher on 2007-10-18
why don't you list the hardware of your PC and we'll go from there

---

### Post by burn3t on 2007-10-19
Mmkay edited the first post

---

### Post by burn3t on 2007-10-20
Hmm well how can I install LILO instead of GRUB?

---

### Post by TGArcher on 2007-10-20
Well, that isn't really the issue. Grub is what is used in Ubuntu and few have really tried to change it. Grub is excellent. I'm still trying to find out how get it running on your hardware. I've never heard of it not working like this because of this kind of issue.

---

### Post by Sef on 2007-10-20
> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

Try [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").  It comes with easy to follow instructions on how to use it.

---

### Post by burn3t on 2007-10-31
I installed Ubuntu from Alternate CD where I chose to install LILO instead of GRUB, so kind of solved now

---

