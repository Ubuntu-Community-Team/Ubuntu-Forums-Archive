---
title: "I cannot  use USB"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by wusitao on 2005-11-14
Today I install ubuntu to my PC. Unfortunately, if I turn on USB function in BIOS, Ubuntu stops at "starting hardware abstraction layer...". 
   But if I turn off the USB function in BIOS, everything is OK. 
   BTW, I can use windows 2000 without the above problem.
   Is there any suggestions?Thanks in advance.


The problem is now solved. I disconnected the line connecting from SCSI controller to CD drive. Then It 's OK. I can use USB now.

---

### Post by makis on 2005-11-14
hi,

may u give us your PC charachteristics (CPU, video cards, motherboard etc). Thus, it would be easyer for someone to help you..

---

### Post by Lambert on 2005-11-14
With the bios seting switched off, have you tried to use a usb device? It may be a seen device by ubuntu but no driver present so ubuntu doesn't know what to do with the device.

How can you test?

plug the device in, open a terminal Applications>accesories>terminal and then type

```
sudo lshw -C bus
``` password is just your password

Look for your device. Look for the Configuration line; driver=??

What does it say here? You can post the whole section on your device here and somebody can try to help you.

---

