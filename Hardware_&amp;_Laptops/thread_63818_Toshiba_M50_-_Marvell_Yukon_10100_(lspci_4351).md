---
title: "Toshiba M50 - Marvell Yukon 10/100 (lspci 4351)"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by gururug on 2005-09-09
Hello Friendly Folk,

Just install 5.04 on Toshiba M50 and doesnt detect 
Marvall Yukon 10/100

All references I have found are for the Gigabit Yukon card
not the 10/100

What is the driver, how to get / do


Already tried;

modprobe sk98lin

but must be wrong driver



P.S. Centrino Wifi Interface is OK on eth0 from
install

---

### Post by gururug on 2005-09-09
Oh and by the way;

anybody know why is the HDD picked up as sda?

---

### Post by 23meg on 2005-09-14
i have a Tecra M4 with a Marvell Yukon gigabit ethernet adapter and it isn't detected either. [this thread](http://ubuntuforums.org/showthread.php?t=47615) may help you. let me know if you have any success.

> Oh and by the way;

anybody know why is the HDD picked up as sda?

probably because it's a SATA drive, which i think is run via SCSI emulation.

---

