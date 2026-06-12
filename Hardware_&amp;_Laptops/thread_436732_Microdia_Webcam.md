---
title: "Microdia Webcam"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by kobolduk on 2007-05-08
I've installed Ubuntu 7.04 and got a Microdia (Coca Cola) webcam. But I can't get it work with Ubuntu. When I do 'lsusb' I see a new device:

```
Bus 001 Device 004: ID 0c45:6011 Microdia 
```
Also when I do 'dmesg', I see

```

[  118.783305] usb 1-1: USB disconnect, address 2
[  120.427286] usb 1-1: new full speed USB device using ohci_hcd and address 3
[  120.632037] usb 1-1: configuration #1 chosen from 1 choice
[  364.154510] usb 1-1: USB disconnect, address 3
[  375.758461] usb 1-1: new full speed USB device using ohci_hcd and address 4
[  375.963051] usb 1-1: configuration #1 chosen from 1 choice

```

I looked at [http://mxhaard.free.fr](http://mxhaard.free.fr) but I can't a manual how to install this, and since I'm new to linux I don't know how to start.

Could someone please help me out here?

---

### Post by mad chey on 2007-05-12
weve got the same webcam and ive downloaded that driver but for the life of me i cannot get any joy no matter what i do, the only how to i found was in french unfortunately :(

---

### Post by scorp123 on 2007-11-28
> **mad chey said:**
>  the only how to i found was in french unfortunately :( And can you post the link to that? Thanks.

---

### Post by wsjohnston1 on 2008-02-19
try this weblink  [http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7)

I have a 0c45:624f Microdia on a Compal EL80 laptop.  I downloaded the SN9CXXX for ubuntu 7.10 from the above link and it works well, although a little darker than I would like (could be my lighting) but clear.  Had a slight problem installing but I am new to this, however, it works somehow!!  Hope this helps.

---

### Post by mlapaglia on 2008-03-10
I got the driver working with my Compal EL80, but the picture is horrendous. The 1.2 megapixel camera takes pictures 4 times the quality in windows. = not paying for it.

---

