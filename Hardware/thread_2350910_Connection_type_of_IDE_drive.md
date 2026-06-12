---
title: "Connection type of IDE drive?"
date: 2017-01-28
forum: Hardware
---

### Post by SchnappiJedi on 2017-01-28
Going to use this old drive for a linux computer. It seems to use some sort of IDE connection and has exactly 45 pins. A few photos are below. What is the correct terminology of the connection type for the drive and will this adapter work to convert it to SATA?

[URL="https://www.newegg.com/Product/Product.aspx?Item=9SIA67038S6812&cm_re=ide_to_sata_44_pin-_-9SIA67038S6812-_-Product"]https://www.newegg.com/Product/Product.aspx?Item=9SIA67038S6812&cm_re=ide_to_sata_44_pin-_-9SIA67038S6812-_-Product
[/URL]

---

### Post by Yellow Pasque on 2017-01-29
I always called it 2.5" PATA and the cable is a 44-pin cable.
The adapter should work.

---

### Post by oldfred on 2017-01-29
You may have to make sure jumpers are set correctly on drive.
It should have master, slave, & cable select. But cable select only works with the 80 pin cable.

 with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

---

