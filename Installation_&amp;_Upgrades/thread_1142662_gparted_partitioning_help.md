---
title: "gparted partitioning help"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by n1h0k3r on 2009-04-29
hi
i am running parted magic os from a usb drive. i am trying to resize a partition that has Ubuntu on it. it is 113 gb before, and will be 35 gb after. i have 24 gb full at the moment. when i try to resize it, it says:
[I]"filesystem is mounted or opened exclusively by another program?
e2fsck 1.41.4 (27-jan-2009)
e2fsck: Device or resource busy while trying to open /dev/sda6"[/I]

i read somewhere that it may be that the os is using the swap (sda6 is in an extended partition, and linux-swap is in the same one) even though i am booting from a usb. is there any way to fix this? or is that not my problem?

---

### Post by logos34 on 2009-04-29
yep, sounds like swap is activated,  Does that automatically a lot

right-click on swap in gparted>swapoff

---

