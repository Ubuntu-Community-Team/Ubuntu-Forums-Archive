---
title: "Mounting a USB hard drive"
date: 2004-11-24
forum: Hardware &amp; Laptops
---

### Post by bogl on 2004-11-24
I have a USB enclosure with two partitons: sda1=FAT32, sda5=ext2.

I am having no end of trouble mounting them.  sda5 seems to automount fine, but sda1 will not at all.  I've googled and tried the following in /etc/fstab:

/dev/sda1 	/mnt/usbdrives	vfat 	rw,exec,user,noauto,umask=000 0 0

but that has proved fruitless too.

I am beginning to think automount simply doesn't work with this drive.  How can I disable it?

Thanks for any help,

bogl

---

### Post by bogl on 2004-12-08
Still struggling with this - no thoughts, Ubuntueenies?  

I wonder if the fact that this drive needs to use two USB ports (special double-headed cable) has some effect, though as I say it works perfectly under Knoppix.

bogl

---

### Post by arctic on 2004-12-08
try the following:

/dev/sda1 /mnt/usbdrives vfat unmask=0,iocharset=iso8859-1,codepage=850 0 0

---

### Post by bogl on 2004-12-10
Thanks for the suggestion.  Still no go, I'm afraid.  Nautlius reports the drive has having the right amount of free space in it, but that's all - no files shown at all.

Most odd.  

Further suggestions welcome!

bogl

---

