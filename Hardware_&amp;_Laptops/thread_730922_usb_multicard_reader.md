---
title: "usb multicard reader"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by dope540 on 2008-03-21
Hi,

I've just installed ubuntu 7.10 onto my home pc and it seemed quite easy, manage to set it all up and install my HP all in one printer.

I even managed to install my iriver H10 mp3 player on there and that usually only works on windows.

I then tried my multicard reader which plugs into the usb, but ubuntu does not recognise this.

sorry if this has been asked, but I am new to ubuntu after being a windows user previously.

---

### Post by AJB2K3 on 2008-03-21
It won't help but my elchepo external works but the internal doesn't.

Plug in the reader, open a terminal and type
```
lsusb
```
and post up the result.

---

### Post by dope540 on 2008-03-29
Hi,

Sorry it took me a while to post the results, been at uni.

heres the results when i typed in lsusb in the terminal:

Bus 004 Device 004: ID 058f:6362 Alcor Micro Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 001 Device 003: ID 056a:0061 Wacom Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

the alcor micro is the multi card usb reader, sunplus is my webcam and the wacom is my tablet pen

---

