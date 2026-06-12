---
title: "Texas Instruments SD card reader"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by huangja on 2007-07-12
Hi, 

I have a Texas Instruments PCI7420 SD/MMC card reader and it mounts perfectly fine on my laptop. However, when I try to copy large files to it, it crashes. I believe it has to do with the computer trying to read the card too quickly, causing it to crash. An error message pops up with something along the lines of "I/O Error". 

I had a similar problem on an mp3 player that connected through usb. I fixed that by changing the value of max_sectors, which I believe sets the maximun packet size for a data transfer to the usb device. Is there any way to do this for the SD card reader? 

Thanks

---

