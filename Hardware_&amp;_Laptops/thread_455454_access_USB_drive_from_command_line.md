---
title: "access USB drive from command line"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by skryn on 2007-05-26
I am trying to get some files off of a USB disk drive, but cannot figure out how to do it. Main problem is, I am stuck in command line. It's formatted in FAT, and I've got Ubuntu Edgy.

Thanks!

---

### Post by phazeman on 2007-05-26
you should try mounting it first (if it's not auto-mounted already). check in /media for usb mounts. if it's not there - try to mount any /dev/sdX (a,b,c, etc...) to somewhere

---

### Post by Ek0nomik on 2007-05-26
Post output for:

```
sudo fdisk -l
```

---

### Post by skryn on 2007-05-27
> **Ek0nomik said:**
> Post output for:

```
sudo fdisk -l
```

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 cylinders/track, 4864 cylinders
Units = cylinders of 16065 *512 = 8225280 bytes

Device 	         Boot		Start		End		Blocks		   Id	   System
/dev/hda1	*		1		4795		38515806        83	Linux
/dev/hda2			4796		4864		554242+		5	Extended
/dev/hda5			4796		4864		554211		82	Linux swap / Solaris

Disk /dev/sda: 4095 MB, 409573856 bytes
128 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes

Device	         Boot	   Start	     End		Blocks		    Id	   System
/dev/sda1			1		992		3999712+           b	W95 FAT32

---

