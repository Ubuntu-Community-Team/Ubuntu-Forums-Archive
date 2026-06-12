---
title: "Usb ubuntu, can i point the casper fil on another usb?"
date: 2011-04-12
forum: Hardware
---

### Post by chezbob on 2011-04-12
Hi, 
I know I cannot boot a usb ubuntu on a mac and pc, so i figured than mayb i can make 1 usb ubuntu bootable from my mac and another usb drive bootable on pc and point each time the location of the persistent casper?

-I have a flash drive of 1 gb, i was thinking putting the Mac bootable ubuntu on it
-I have a 16 gb drive, I was thinking of putting the Windows bootable ubuntu on it, AND the persistent casper file on it ( on another partition mayb?)

Tell me if its possible to point the casper partion in ubuntu , so i can boot from either the mac or windows, then save the work and programs on the same casper file, so I can work with my programs in any environnement, mac or pc, with the use of 2 key?

I am not a total expert in linux, can you help me?
Thank to the linux community.

---

### Post by C.S.Cameron on 2011-04-12
Live Ubuntu should be able to find any casper-rw file or partition in it's path.
To make persistent select disk / syslinux / text.cfg and add "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

---

