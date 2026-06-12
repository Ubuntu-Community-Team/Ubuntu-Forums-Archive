---
title: "Need help with Natty and BR Drive"
date: 2011-07-27
forum: Hardware
---

### Post by dothedog on 2011-07-27
All, I have a new computer I built recently and installed Natty with the Unity Desktop. Kind of getting used to the new Mac-y look and feel. In any event, the problem I am having is that the Blu-Ray Drive is not being detected/mounted.

Here are the specs
MSI H61M-P23 B3 Intel H61 Motherboard
Intel Core i3-2100
Corsair 4GB DDR3 RAM
Seagate 1TB LP Serial ATA HD 5900/32MB/SATA-3G
Asus GeForce GTX 460
LG BH10LS30 Blu-ray Drive

It is showing in the bios, I have the SATA settings to IDE.

dmesg shows this.

```
[    2.921759] ata2.00: ATAPI: HL-DT-ST BD-RE  BH10LS30, 1.00, max UDMA/133
```

If I insert a disk, nothing shows up, /dev/sr0 is not created, nautilus doesn't show anything. 

I do dual boot with Win7 so I know that the drive is physically working.

Any and all help is appreciated.

DoTheDog

---

### Post by dothedog on 2011-07-28
Anyone?

---

### Post by dothedog on 2011-07-28
No Ideas?

---

### Post by dothedog on 2011-07-28
Solved it by changing the SATA connector on the MB. Not sure why that fixed it though.

---

