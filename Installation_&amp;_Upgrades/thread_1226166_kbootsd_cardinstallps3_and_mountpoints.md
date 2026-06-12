---
title: "kboot/sd card/install/ps3 and mountpoints"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by jacabmou on 2009-07-29
Hi all..

I found my "old" ps3 in the basement, and now i want to install the latest ps3-ubuntu.

My problem is that the cdrom, is broken, so i cant use my burnd cd.

I have then put ubuntu iso/files on a 1 gb sd card.

I then boot up the kboot manager and mount my sd card in /mnt/usb.

Now, my ? is, how do i install from /mnt/usb?

Thanks
Jacob

---

### Post by stlsaint on 2009-07-29
check here...just as a start if still need help post again! 
[www.pctipsbox.com/ubuntu-710-on-ps3](www.pctipsbox.com/ubuntu-710-on-ps3)

---

### Post by jacabmou on 2009-07-29
i found it


kexec -f --append="root=/dev/ps3da1" /var/tmp/mnt/ps3da1/boot/vmlinux

---

