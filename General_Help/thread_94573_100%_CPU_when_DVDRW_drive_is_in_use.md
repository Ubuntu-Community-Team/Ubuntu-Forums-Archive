---
title: "100% CPU when DVDRW drive is in use"
date: 2005-11-24
forum: General Help
---

### Post by digitalkarabao on 2005-11-24
Everything is working fine except when the disc drive is in use, CPU usage shoots to 100% and my system crashes and shuts down.

---

### Post by frodon on 2005-11-24
Maybe you need to enable DMA on your disk drive : [http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

### Post by digitalkarabao on 2005-11-24
I enabled DMA from day 1 of the breezy installation. I suspect it is not really the drive. The portable gets hot and I guess, overheats when the drive is in use shooting up at 100%CPU usage causing the portable to crash and burn.

---

### Post by cdsboy on 2005-11-24
maybe its an program error that makes your cpu thinks it needs 100%. try throttling your cpu to half and see if that does it.

---

### Post by smgil on 2005-11-24
This could work, just change the dev name.

sudo hdparm -d1 /dev/hdc

---

### Post by digitalkarabao on 2005-11-24
bad thing. my CPU does not support scaling. it is always maxed out at 3GHz. argh!

---

