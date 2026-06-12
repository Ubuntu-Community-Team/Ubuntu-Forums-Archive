---
title: "/dev/sda becomes /dev/sdb after connecting second SATA disk"
date: 2006-08-06
forum: Hardware &amp; Laptops
---

### Post by gwi on 2006-08-06
I have one harddisk (a SATA disk) in my computer. Ubuntu sees it as /dev/sda.
For backups I have an external SATA disk. When I plug it in, there is a syslog message
```
nv_sata: Secondary device added
```
Nothing more happens. It seems that the current kernel (I am using 2.6.15-26-amd64-k8 ) does not support hot-plugging.

When I try to boot with the external disk plugged in, Grub comes up (from the first disk). I can select Ubuntu, and the splash screen is shown (also from first disk). It then says
```
Mounting root file system ...
Waiting for root file system ...
```
After a few minutes I end up at a Busybox prompt. Looking in /dev I can see that my first disk is now /dev/sdb, where it should be /dev/sda.

My BIOS shows my first disk as "first SATA master", so that's ok. Booting Grub is ok, so up to here no reversed disk order.

What is causing the incorrect order when Ubuntu tries to boot, and how can I solve it?

There was a similar thread, saying in the BIOS the "IDE compatibility settings" should be changed from "Enhanced" to "Compatible". But I can't find that setting in the BIOS of my motherboard (Asus A8N SLI DeLuxe).

The external harddisk is my backup device. I have used it in Windows without any problem. In Ubuntu I now can not make backups, and I don like that!

---

