---
title: "Non booting IDE drive?"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by laidback on 2007-11-01
I have a Western Digital 40 Gb IDE drive that is causing problems. I can load Ubuntu onto it but then it simply refuses to boot. Gparted says all is OK, but...BIOS is very slow to detect it and CMOS reports a different size (29Gb)! I've reformatted several times to no effect. Seems that it thinks it's a different beast to that reported by Gparted or detected by the Ubuntu installer (but then that's Gparted as well I suspect). I've had it from new and this is the first time I've tried to use it in earnest. I have previously installed it in a USB hdd system and stored data on it, that went OK. 

Is it a dead beast?

Many thanks

---

### Post by ROBarber on 2007-11-02
maybe you should set a boot flag for that partition, using gnome partition manager.
also a fsck scan maybe will show which sectors of your harddrive are bad.

---

### Post by laidback on 2007-11-02
ROBarber,

Thanks for responding. Boot flag is set and I checked it with Gparted as you suggest.
Have run Test Disc against it, no bad sectors, it passes. In fact when I look at the hdd with Gparted (I have the bootable version) all seems well, size is correct, boot flag is set, partitions are as I'd expect after a fresh install from a Live Ubuntu CD. It just doesn't boot at power up, and the BIOS/CMOS has it at 29Gb rather than 40Gb, plus it takes ages before the hdd is recognised at boot up. And it refuses to boot.

---

### Post by ROBarber on 2007-11-02
Did something wrong came up with your PC configuration, like a hit or some electric overpower? Did you check the jumpers of your hdd? can you show what's in your fstab file?

---

