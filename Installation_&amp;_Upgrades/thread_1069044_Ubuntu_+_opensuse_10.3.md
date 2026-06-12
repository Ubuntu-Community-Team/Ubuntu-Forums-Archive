---
title: "Ubuntu + opensuse 10.3"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by ehsan.s on 2009-02-13
hi. I have a problem with double Linux system
I've installed ubuntu and opensuse10.3. ubuntu's grub doesn't boot opensuse and opensuse's grub doesn't boot ubuntu and windows.
when I need opensuse I have to write :
```

sudo grub
root (hd0,8)
setup (hd0)

```
on ubuntu's terminal that hd0,8 is the partition that opensuse has been installed on it.
and when I need ubuntu or windows I have to boot live ubuntu and change the boot menu by similar command.
I think this is a big trouble.:-k

---

### Post by Pumalite on 2009-02-13
Edit menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
Mount the other partition, open menu.lst and copy paste in the original menu.lst

---

