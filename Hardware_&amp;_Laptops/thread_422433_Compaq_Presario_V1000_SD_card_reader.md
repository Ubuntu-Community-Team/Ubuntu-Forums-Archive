---
title: "Compaq Presario V1000 SD card reader"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by apsivam on 2007-04-25
I've a Compaq Presario V1000 with Feisty installed. How can I make my SD card work with it. When I insert SD card on the slot it gets detected by the kernel (verified it by logtailing /var/log/message) but not getting mounted. I've also tried the other method mentioned here (the setpci thing) with no luck.

---

### Post by clueless dave on 2007-05-06
I have a different setup, but found a really simple workaround that might be worth trying.   Turns out that I had formatted the SD card on my Palm, which created no problem in Edgy. But try as I might I couldn't get the card to mount - auto or otherwise even though the system recognized that a card had been inserted in the reader.

 I tried reformatting the SD card in my digital camera (presumably to vfat) and it mounted fine.  If you have a new SD card around, or have a digital camera with an SD card you could reformat, you might try that and see what happens.  If it works you can get back to more fun things.

No guarantees, but I'm glad I tried it - it's easy and it avoided the risks of messing up something else on my system.

If it doesn't work check around some of the hardware forums.  It seems a lot of folks are having trouble with their card readers, and esp. USB devices, after upgrading to Feisty (whether it's a Feisty issue or a kernel issue is still a bit up in the air).

---

