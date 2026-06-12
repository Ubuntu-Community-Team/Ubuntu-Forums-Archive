---
title: "kernel patch can't find bcm43xx_main.c"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by DrPppr242 on 2007-08-07
I'm trying to patch my driver for the broadcom wifi card in my laptop to support packet injection but the patch is suppose to patch a file in 
/usr/src/linux-headers-2.6.20-16/drivers/net/wireless/bcm43xx/
that directory exist but only contains Kconfig and makefile not bcm43xx_main.c, does anyone know how to patch this driver?

---

### Post by MrSootentai on 2007-09-01
I know this is old but I am going to bump this because I need help too!

---

### Post by nick_h on 2007-09-02
If you download the kernel source it willl contain bcm43xx_main.c

---

