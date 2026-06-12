---
title: "NCQ on sata drive"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by kingmoffa on 2007-06-06
Hello all, 

I have recently upgraded my media server box from edgy to feisty (impressed nothing major broke) as I wanted NCQ support for my media HDD. 

However, I am having problems enabling NCQ. (one  of the main reasons I moved to feisty for the updated kernel). 

I've used the webpage: [http://linux-ata.org/faq.html](http://linux-ata.org/faq.html) to guide me.

I have the line
[   34.963091] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
in my dmesg

However, when trying to increase the queue depth I have permission denied errors. 


:~#  echo 31 > /sys/block/sda/device/queue_depth
bash: /sys/block/sda/device/queue_depth: Permission denied

I've changed a setting in the bios for sata from enhanced to compatibility , it has not had an effect. (its back on enhanced now).  My m/b is a Asus P5GZ-MX (intel ich6) with a new Seagate 7200.10 SATAII/300 drive. 

Any suggestions would be helpful.

---

### Post by kingmoffa on 2007-08-08
bump

---

