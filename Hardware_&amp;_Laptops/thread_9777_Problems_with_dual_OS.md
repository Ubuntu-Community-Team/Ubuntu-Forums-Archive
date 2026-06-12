---
title: "Problems with dual OS"
date: 2005-01-01
forum: Hardware &amp; Laptops
---

### Post by Verr on 2005-01-01
So I had winxp installed on my comp and I decided to istall ubuntu also. So I resterted my comp with ubuntu CD. I partitied my hard disks and now they look like this :




Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            9605        9729     1004062+   f  W95 Ext'd (LBA)
/dev/hda2   *           1         461     3702951    b  W95 FAT32
/dev/hda3            7781        9604    14651280   83  Linux
/dev/hda5            9605        9729     1003968   83  Linux

I explain a bit. This first should be my winxp at c:. Second is d: which is recovery partition for winxp. Third is for my linux and fourth is my swap.

So when I go to grub and choose winxp I get this error:

Windows could not start because of computer disk hardware configuration problem. Could not read from the selected boot disk. Check boot path and disk hardware. Please check windows documentation about hardware disk configuration and your hardware reference manual for additional information.

What should I do? I think that i made some partitions wrong. Can someone help me and tell what to do, i really need windows too.

---

