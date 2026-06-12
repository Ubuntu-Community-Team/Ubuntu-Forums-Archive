---
title: "Hardware Monitoring / Mainboard: MSI 945 P"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by Camino on 2006-11-09
Hi Community,
I would like to know, if there is a solution for Dapper Drake to monitor the hardware of the mainboard MSI 945P Neo3 installed with CPU Intel E6300 Dual 2 Core

[http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=754](http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=754)

At the moment I got installed Gkrellm 2.2.9 and could get the info of the cpu speed and NVIDIA GPU temperature. 

But I would like to see some more infos, like fan rpm, cpu temp, system temp,...

Any ideas ?

The specs of the board are:

> 
Supports Socket 775 for Intel® Core 2 Duo, P4 5XX, 6XX, P4EE, Pentium D 8XX, 9XX and Celeron D processors.
• Supports FSB 1066/800/533MHz.
• Supports EIST technology.
• Supports Intel® Hyper-Threading technology.
• Supports Intel® Dual Core Technology to 800MHz and up.



> 
Chipset

• Intel® 945P Chipset
- Supports FSB 533/800/1066MHz.
- Supports PCI Express x 16 graphics interface.
- Supports dual channel, DDR2 400/533/667 (4GB Maximum)

• Intel® ICH7 Chipset
- Hi-Speed USB (USB2.0) controller, 480Mb/sec, up to 8 ports.
- 4 SATAII ports with transfer rate up to 3Gb/s.
- 1 channel Ultra ATA 100 bus master IDE controller.
- PCI Master v2.3, I/O APIC.
- ACPI 2.0 compliant.
...
and much more :)


With regards

Camino

---

### Post by THaugland on 2006-11-09
I think that you should look at [http://www.lm-sensors.org/](http://www.lm-sensors.org/). While your motherboard is not on the list of supported motherboards, it might still give you useable results. Look at [http://www.die.net/doc/linux/man/man1/sensors.1.html](http://www.die.net/doc/linux/man/man1/sensors.1.html)

---

### Post by Camino on 2006-11-10
thanks for your response !

I tried to use the lm-sensors but I only got the message "no sensors available;reload the kernel modules". I installed from repository (2.9.2) and also from source (2.10.1). Modprobed the recommend modules but it´s not working at all. 

Seems like the board is not supported yet...too bad

---

