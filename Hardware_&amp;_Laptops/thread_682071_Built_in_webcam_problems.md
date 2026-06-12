---
title: "Built in webcam problems"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by omgapolarbear on 2008-01-29
Ok, I'm using a HP dv6000 and I've gotten the drivers up and running for the internal webcam, but when I go to start up camorama it doesnt detect it. It says "could not connect to video device (/dev/video0) please check connection"

Help?

---

### Post by jcwmoore on 2008-01-29
I have the same issue as well, only on an HP dv2000...

personally I have never really tried to fix it, it really isn't that big a deal to me...

---

### Post by omgapolarbear on 2008-01-29
BTW lsusb came up with ```
Bus 002 Device 002: ID 0c45:62c0 Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 
```

---

### Post by omgapolarbear on 2008-01-31
someone please help

---

### Post by intel on 2008-02-01
Microdia 
(Webcam Support group for all Microdia chipsets under Linux)
Q) Is my webcam a "microdia"? 
A) Execute the following command 
    #lsusb
If you see any of the following numbers, you have a "microdia" webcam

0c45:6027, 0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:6242, 0c45:6253, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:62c0, 0c45:8105

(basically 0c45:<xxxy> above is enough to conclude you have a microdia webcam) 
All of the above webcams are unsupported under Linux

https://groups.google.com/group/microdia

Please join this Group, to help each other get better support for these webcams from Linux.

---

### Post by vivalant on 2008-02-01
Microdia webcams are supported under Linux. A driver is already available at [http://www.linux-projects.org](http://www.linux-projects.org)

---

