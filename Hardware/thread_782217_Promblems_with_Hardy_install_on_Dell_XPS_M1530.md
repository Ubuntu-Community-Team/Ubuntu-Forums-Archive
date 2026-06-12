---
title: "Promblems with Hardy install on Dell XPS M1530"
date: 2008-05-04
forum: Hardware
---

### Post by phamnewan on 2008-05-04
XPS M1530 with following hardware:

XPS M1530, Intel Core 2 Duo Processor T8300 (2.4GHz/800MHzFSB, 3M L2 Cache)
256MB NVIDIA GeForce 8600M GT
250GB 5400RPM SATA Hard Drive for XPS M1530

I verified hardware worked by booting vista one time. Everything worked. 8.04 Hardy 64-bit install had two problems:

Touchpad will only work about 1 boot in 10.
Wireless is not on and I have been unable to get it going.

I know ubuntu ok, but no expert.  Doing the recovery with the Xserv fix gets the touchpad working for that boot, but not the next.  Please help.

---

### Post by slyhne on 2008-05-05
Hi phamnewan

I had the same problems with my touchpad, but fixed it by adding this to my /boot/menu.lst

i8042.nomux=1

My boot section looks like this for my Dell XPS M1530:

> title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=8971ac7c-256e-471b-b415-0e33249223ad ro quiet splash noapic i8042.nomux=1
initrd /boot/initrd.img-2.6.24-16-generic
quiet

You can edit /boot/grub/menu.lst by doing this:

```
sudo gedit /boot/grub/menu.lst
```


Regards

Slyhne

PS: the noapic helps the wireless to work better!

PPS: If you want even better wireless (if you have the Intel 3945 card), then try installing linux-
backports-modules-2.6.24.

```
sudo apt-get install linux-backports-modules-2.6.24
```

---

