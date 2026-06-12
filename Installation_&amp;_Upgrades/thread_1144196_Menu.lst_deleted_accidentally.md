---
title: "Menu.lst deleted accidentally"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by gsiliceo on 2009-04-30
Hi, i accidentally deleted my menu.lst from the boot folder and i don't know how to rebuild it, i've tried some i found online but none have worked so far.

I'm in the ubuntu live cd.

Where should i start?

Ubuntu 9.04 is installed no kernel upgrades and this is my fstab 
# / was on /dev/sdb6 during installation
UUID=3263ce84-8abd-4d9a-a202-599321067920 /               ext4    relatime,errors=remount-ro 0       1
# /media/ALMACEN was on /dev/sda2 during installation
UUID=CCB05257B05247DA /media/ALMACEN  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /media/COMPARTIDO was on /dev/sda1 during installation
UUID=4772-52F1  /media/COMPARTIDO vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sdb5 during installation
UUID=9d0c82fb-6468-4d5a-b5e1-d517d9f68028 none            swap    sw              0       0

---

### Post by taurus on 2009-04-30
Is root filesystem, /, on /dev/sdb6?  See if there is a backup file.

```
sudo mkdir /media/ubuntu
sudo mount -t ext4 /dev/sdb6 /media/ubuntu
ls -la /media/ubuntu/boot/grub
```

---

### Post by gsiliceo on 2009-04-30
Yeah thats it.
SOrry no backup there. I really need to rebuild that

---

### Post by taurus on 2009-04-30
```

default		0

timeout		3

title		Ubuntu 9.04, kernel 2.6.28-11-generic
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3263ce84-8abd-4d9a-a202-599321067920 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

```
Try that and see if it works.

---

### Post by sisco311 on 2009-04-30
to boot the system:

in the grub boot menu press c to switch to the grub command prompt

assuming that sda1 is your root "/" partition type:
```
root (hd0,0)
kernel /boot/vmlinuz<hit TAB for auto-completion> root=/dev/sda1
initrd /boot/initrd.gz<hit TAB>
boot
```


use
```
sudo update-grub
```to generate a new menu.lst file.

---

