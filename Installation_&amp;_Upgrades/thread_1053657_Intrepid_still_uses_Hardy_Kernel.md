---
title: "Intrepid still uses Hardy Kernel"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by revcol on 2009-01-28
Upgrade from hardy to intrepid went well, however grub continues to show and load kernel 2.6.24-21-generic. All updates are current. Synaptic shows all kernels thru 2.6.27-11.14 loaded and installed. System appears stable, is this  normal?

---

### Post by cariboo on 2009-01-28
No it's not normal, you probably  told the installer to leave grub as it was instead of the letting the installer use the maintainers version. You could probably add the new entries manually, or I would try:

```
sudo dpkg-reconfigure linux-iamge-generic
```

to see if that updates grub.

Jim

---

### Post by tommcd on 2009-01-28
First, backup your current menu.lst:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
Then run:
```
sudo update-grub
```
to update the kernel entries in menu.lst.

---

