---
title: "Recover data from harddrive using live cd."
date: 2008-07-22
forum: General Help
---

### Post by koga on 2008-07-22
Hi, im in need of a little help.
I was playing around trying to install ubuntu on a usb stick and without paying enough attention while following a how-to i think i broke my Hardy Heron install with FDISK commands from the terminal. I was trying to format the usb stick to get a boot loader working and stuffed things up. When i restarted my pc it came up with "no operating system installed" or something similar. 

I have tried the Super Grub boot disk and G-live/testdisk for the past few hours with no joy. I have two hard disks in my pc, a 250g which had ubuntu installed and a 80g with XP. I can see both these disk's from the "Places" menu when i run from the live cd but i cannot mount my ubuntu disk to recover my data (i can mount and access the XP drive though).

When i try to mount the ubuntu drive i get the following error message.
"Cannot mount volume"
"Details"
"mount:wrong fs type,bad option,bad superblock on /dev/sda1, missing codepage or helper program, or other error. In some cases useful info is found in syslog -try dmesg tail or so"

Any help would be really appreciated and if i need to give some more info or explain anything just say so.

Cheers,

---

### Post by pauper on 2008-07-22
Are you sure you're mounting the correct partition?

```
sudo fdisk -l
```

[http://www.mjmwired.net/kernel/Documentation/devices.txt#195](http://www.mjmwired.net/kernel/Documentation/devices.txt#195)

Do you specify file system type, i.e. "-t vfstype"? For example,

```
sudo mount -t ext3 /dev/sda1 /media/disk
```

Look into dmesg and syslog output right after mounting fails for errors.
Try searching the web with that particular error message. 

[http://www.mail-archive.com/jfs-discussion@lists.sourceforge.net/msg00412.html](http://www.mail-archive.com/jfs-discussion@lists.sourceforge.net/msg00412.html)

```
man fsck
```

---

