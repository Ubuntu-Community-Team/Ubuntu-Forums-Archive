---
title: "Grub Read Error - After Ubuntu 8.0.4 Install"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by stechkov on 2008-12-06
i am getting an error "Grub Read Error" After installing Ubuntu 8.0.4 using USB FLASH DRIVE... i dont know why.. installed it alone now windows or anything just ubuntu.. please help me...

---

### Post by stechkov on 2008-12-06
just reseted my CMOS Settings now im getting

Grub Stage Loading 1.5 Error

---

### Post by caljohnsmith on 2008-12-06
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

---

