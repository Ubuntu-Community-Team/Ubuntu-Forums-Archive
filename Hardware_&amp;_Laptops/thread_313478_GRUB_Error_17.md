---
title: "GRUB Error 17"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by quintok on 2006-12-06
When it works:
1 Primary Master hdd
1 Secondary Master hdd
1 Secondary Slave dvd

When it doesn't:
1 Primary Master hdd <-- has windows and grub bootloader on it
1 Primary Slave hdd <-- has windows on it
1 Secondary Master hdd <-- linux
1 Secondary Slave dvd

What I think it is:
I think the problem is it's slotting between primary and secondary master in the drive letter allocation which then stuffs up when it goes to grub's menu.lst which then refers to hd0 and hd1 but I don't know how to get around that and still allow me to boot at all if I stuff it.

Boot Info:
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (single-user mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, kernel 2.6.17-9-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-9-generic root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-9-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-9-generic (single-user mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-9-generic root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-9-generic
boot

title		Ubuntu, kernel 2.6.17-8-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-8-generic root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-8-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-8-generic (single-user mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-8-generic root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-8-generic
boot

title		Ubuntu, kernel 2.6.17-7-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-7-generic root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-7-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-7-generic (single-user mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-7-generic root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-7-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Thanks.

---

### Post by Sef on 2006-12-06
From the [Gentoo error collection]("http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap5"):

> 5. Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Be sure to check your root(x,y) settings in your grub.conf.

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it.

6. 

---

