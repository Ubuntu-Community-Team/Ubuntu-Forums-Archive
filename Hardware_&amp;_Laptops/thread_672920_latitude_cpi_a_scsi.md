---
title: "latitude cpi a scsi"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by carpman on 2008-01-20
Hello. ok i have installed xbuntu on a dell latitude cpi a 366mhz all seems to work fine except the hard drive is seen as scsi drive sda. What this means is that i cannot use hdparm to optimise harddrive.


This just plan ide laptop drive and is not scsi, how can i use hdparm?


cheers

---

### Post by K.Mandla on 2008-01-20
[sdparm]("http://packages.ubuntu.com/gutsy/admin/sdparm")?

Although to be honest, I used to run Ubuntu and a couple of other distros on a CPi-A 300Mhz, and hdparm is still what I used. That /dev/sda label is ... just a label, I believe.

---

### Post by carpman on 2008-01-20
> **K.Mandla said:**
> [sdparm]("http://packages.ubuntu.com/gutsy/admin/sdparm")?

Although to be honest, I used to run Ubuntu and a couple of other distros on a CPi-A 300Mhz, and hdparm is still what I used. That /dev/sda label is ... just a label, I believe.


Suppose what thinking is why is it sda?

Also this prevents apps such as linHDD working

---

### Post by carpman on 2008-01-20
hdparm does not seem to work



 hdparm -c1 -d1  /dev/sda

> /dev/sda:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 IO_support    =  0 (default 16-bit)

---

