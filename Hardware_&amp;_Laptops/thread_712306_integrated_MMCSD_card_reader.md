---
title: "integrated MMC/SD card reader"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by amarant on 2008-03-01
My Inspiron 1525 have a built in MMC/SD card reader, the reader is listed in the device manager but don't seem to be able to mount it :S

when i do a:
sudo mount /sys/class/mmc_host/mmc0 /media/mmc

i get an error saying that it is not a block device.

Am i missing a driver?

---

### Post by crazedgremlin on 2008-03-02
When you put a card into  your card reader, it *should* automount.

If you're doing it manually, don't mount /sys/class/mmc_host/mmc0

the card you're looking for will be somewhere in /dev

---

### Post by amarant on 2008-03-03
Ok, it doesen't automount, i'll try looking for it in /dev

---

### Post by amarant on 2008-03-03
It turned out that SD cards auto mount while MMC cards do nothing, ah well i consider this case closed since SD cards are what i will use.

---

### Post by quill7111 on 2008-03-28
I do use MMC cards, and I have the same issue of SD cards mounting automatically when inserted into my integrated reader but nothing happening with MMC. Anyone have an explanation/fix?

---

