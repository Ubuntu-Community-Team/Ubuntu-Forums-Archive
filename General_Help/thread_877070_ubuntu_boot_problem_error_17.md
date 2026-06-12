---
title: "ubuntu boot problem error 17"
date: 2008-08-01
forum: General Help
---

### Post by ch1902 on 2008-08-01
Hi, I'm having problems trying to set up Ubuntu 8.04 on an external hard drive. During the install process I chose to use the whole disk (160GB) rather than create a partition and when it came to installing grub I used the advanced option to make sure it was installed to the external hd (I'm guessing that's where my meddling caused the problem).

Now when I turn my laptop on I press F12 to choose where to boot from (I don't mind doing that, I prefer Windows starts automatically). I choose USB Memory and then I get a screen that lists Ubuntu twice, a memory test and Windows Vista in the other OS list. When I choose either of the Ubuntus it gives me the following error.

Error 17: Cannot mount selected partition

I've read a lot of threads here about the error 17 error but I'm not familiar with linux and I'm not sure what to do next. Using the live cd this is the output of fdisk -l

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe249fa65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        7458    58368000    7  HPFS/NTFS
/dev/sda3            7458       14594    57314304    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19083   153284166   83  Linux
/dev/sdb2           19084       19457     3004155    5  Extended
/dev/sdb5           19084       19457     3004123+  82  Linux swap / Solaris

```

This is the end of my menu.lst

```

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1b6fc625-4cf4-4f64-8e56-fa691646436e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1b6fc625-4cf4-4f64-8e56-fa691646436e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1

```

---

### Post by caljohnsmith on 2008-08-01
Many times an error 17 is because Grub sees the order of your HDDs as different then your BIOS sees them. One way to fix it is to modify the (hd1,0) entries in menu.lst, and probably changing them to (hd0,0) will make it work. A more elegant solution is to modify /boot/grub/device.map so that Grub sees the order of your HDDs as the same as BIOS. It should be really easy to do with only two HDDs. Here is info on how to do it:
[http://users.bigpond.net.au/hermanzone/p15.htm#device.map](http://users.bigpond.net.au/hermanzone/p15.htm#device.map)

---

