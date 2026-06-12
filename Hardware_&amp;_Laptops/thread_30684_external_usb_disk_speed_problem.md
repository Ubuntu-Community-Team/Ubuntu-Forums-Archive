---
title: "external usb disk speed problem"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by 23meg on 2005-04-29
before i did a complete reinstall of Hoary a week ago, my external iomega usb 2.0 disk was running at its regular speed. today, while i was browsing images i took with my digital camera with GQView, i noticed that the loading times were very slow (about 3 seconds for 1 - 1.5 mb jpeg files), so i tested the drive speed with hdparm, and got values of about 700 mbps cached and 18mbps buffered read times. 

these values are more or less the same as those i get with my internal laptop drive, which should normally be much slower than the external one. i recall testing them both before with hdparm and the speed of the external drive was equal to 1.5 to 2 times that of the internal one. i know hdparm's speed indications are somewhat varying and inaccurate, but i'm sure i tested many times and averaged the results, and the difference between the drives was very noticeable, both in numbers, and in feel of usage.

since the current speed of the drive when browsing images sequentially resembles very much the speed i get in windows **before** i install my usb 2.0 drivers, i'm under the impression that the drive is working as a usb 1.0 device in Hoary right now for some reason. how can i make sure that it's recognized as a usb 2.0 device?

i've tried enabling DMA for the drive, but no luck:

> $ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument
 

i can't get info on which dma mode the drive is using, its MaxMultSect value, etc. , since it's not responding to the -I parameter either:

> $ sudo hdparm -I /dev/sda

/dev/sda:
 HDIO_DRIVE_CMD(identify) failed: Invalid argument
 

any suggestions?

---

### Post by 23meg on 2005-05-03
will using piix at /etc/modules help with enabling dma for this device? any other ways? it seems hdparm cannot communicate with it at all.

---

### Post by Ringwraith82 on 2008-06-20
Same problem here except i use Hardy Heron with the latest kernel(2.6.24-19). Did you find a solution?

---

### Post by 23meg on 2008-06-21
This is an ancient thread. If I recall correctly, the problem was fixed in either the next kernel update, or a kernel I had compiled myself, but it's been more than three years since I've had it, and I have no idea what precisely fixed it.

---

