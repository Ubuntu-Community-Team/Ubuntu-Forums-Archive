---
title: "Windows Vista/Longhorn (loader) loops"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by mbwmex on 2008-12-11
Did a fresh install of 8.10 via live cd, downloaded on a Dell E1505 running Vista.

When attempting to access Vista via Grub by selecting Windows Vista/Longhorn (loader), it just loops back to Grub menu.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   158246911    79122432    7  HPFS/NTFS
/dev/sda2       158246912   212332543    27042816    7  HPFS/NTFS
/dev/sda3       212332544   258298039    22982748    7  HPFS/NTFS
/dev/sda4       258301951   312576704    27137377    f  W95 Ext'd (LBA)
/dev/sda5       258301952   259507447      602748   83  Linux
/dev/sda6       259514073   310295474    25390701   83  Linux
/dev/sda7       310295538   312576704     1140583+  82  Linux swap / Solaris

    title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		c330152e-fe35-4243-9a02-e98265a03a1f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c330152e-fe35-4243-9a02-e98265a03a1f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		c330152e-fe35-4243-9a02-e98265a03a1f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c330152e-fe35-4243-9a02-e98265a03a1f ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c330152e-fe35-4243-9a02-e98265a03a1f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c330152e-fe35-4243-9a02-e98265a03a1f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c330152e-fe35-4243-9a02-e98265a03a1f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c330152e-fe35-4243-9a02-e98265a03a1f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c330152e-fe35-4243-9a02-e98265a03a1f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

Thanks for any help.

---

### Post by caljohnsmith on 2008-12-11
If Vista is indeed on your sda1 partition, then your Grub menu entry for Vista is fine; that means most likely what happened is you accidentally installed Grub to the boot sector of your Vista partition at some point, maybe during the Ubuntu installation by having Grub installed to /dev/sda1. If that's the problem, fortunately the fix is usually easy; just boot your Windows Vista Install CD, go to the command line, and do:
```
bootrec /fixboot
```
And that will most likely be all it takes to get Vista working again. If you don't have a Vista Install CD that came with  your computer, you can instead download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") and use that instead. Let me know how it goes. :)

---

### Post by meindian523 on 2008-12-11
deleted

better people are in charge :)
<and as an aside to the OP,it's not because of the beans,please don't tend towards judging people's answers by the number of beans they have>

---

### Post by monoiz15 on 2009-03-29
i kinda have the same problem. i have a 250 gig hd in my laptop and vistas taking up like 140 n then i have ubuntu on a 100 gig partition n then another 10 gig partition with ubuntu as well. somehow vista got messed up like with the bootloader or something.. the vista install disc wont work and neither did that command.. it loads the little bar at the bottom, flashes the blue screen, and dies. help??  thank you :)

---

