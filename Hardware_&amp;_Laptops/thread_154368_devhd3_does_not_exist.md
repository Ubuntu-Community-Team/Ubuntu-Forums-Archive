---
title: "/devhd3 does not exist"
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by rrstiff on 2006-04-02
I have installed Ubuntu Brezzy Badger on dozens of desktop, server, and laptop configurations with little or no difficulty, but this one has me stumped:

It is on an Athlon XP 3200+ computer with 1 GB memory, a 200 GB Western Digital HDD with Windows XP Pro on the 1st NTFS partition (100GB), and no partition or formatting on the remaining 100 GB.  There is also a DVD-ROM drive and a DVRW drive.  Every time I try to install Ubuntu on the free space, choosing default settings, I receive the following message upon 1st bootup with GRUB:

Booting 'Ubuntu, kernel 2.6.12-9-386'



	root (hd0,2)

Filesystem type is ext2fs, partition type 0x83

kernel /boot/vmlinuz-2.6.12-9-386 root=dev/hd3 ro quiet splash

	[Linux-bzImage, setup=0x1c00, size=0x124b1b]

initrd /boot/initrd.img-2.6.12-9-386

	[Linux-initrd @ 0x1fb3a000, 0x4b562b bytes]

savedefault

boot

Uncompressing Linux... Ok, booting the kernel.

Loading, please wait...

ALERT! /devhd3 does not exist. Dropping to a shell!

I am a relative Linux Newbe, and the answer might be cleaqr to someone in this message, but I do not yet fully comprehend it.

What do I need to do to get Ubuntu to successfully dual boot with WinXP on this computer?  I sure would appreciate the guidance!  Thank you.

---

### Post by Sutekh on 2006-04-03
[QUOTE=rrstiff]
kernel /boot/vmlinuz-2.6.12-9-386 root=**dev/hd3** ro quiet splash

...

ALERT! **/devhd3** does not exist. Dropping to a shell!
[/QUOTE]
I'm going to assume that you copied this exactly.  The error is happening because of an error in the kernel line, see the bold.  That should be /dev/hda3.  Its missing the '/' and the 'a'.

When the GRUB menu appears, move to the option that needs the correcting and press 'e' to edit.  Go to the line that needs editing and change it so the '/' and 'a' are included.  The line should look like this
```

kernel /boot/vmlinuz-2.6.12-9-386 root=**/**dev/hd**a**3 ro quiet splash
```
When this is done use 'b' to boot.

If this works then you can make the change permanent by editing GRUB's menu; /boot/grub/menu.lst.  But I'll wait until you get that far first.

---

### Post by Sef on 2006-04-03
Have you read this excellent tutorial by Herman on Dual Booting?

[http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")

---

### Post by rrstiff on 2006-04-03
Thank you, Sutekh, your observation of "a" rather than "e" was where I was missing it, and I had no problem editing the GRUB/Menu.lst using sudo to make the change permanent.

---

### Post by rrstiff on 2006-04-03
Thank you, Sef, the tutorial site you recommended looks like a great resource for future use.  I have bookmarked it, and am reading from it now.  Much appreciated.

---

