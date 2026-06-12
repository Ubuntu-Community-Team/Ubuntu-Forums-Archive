---
title: "Bus 001 Device 002: ID 0c45:602a Microdia Meade ETX-105EC Camera compatible?"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by gammyhand on 2006-11-22
Is my webcam which in lsusb comes up as thus:

Bus 001 Device 002: ID 0c45:602a Microdia Meade ETX-105EC Camera

able to work on ubuntu? If so how do I install it?

---

### Post by nicolaw1 on 2008-01-26
I have the same webcam. Will I be able to use it on Kubuntu? If not, what webcams would work on it? Thanks

---

### Post by vivalant on 2008-01-26
You may want to try the SN9CXXX (don't confuse with SN9C1xx) driver at [http://www.linux-projects.org](http://www.linux-projects.org) . Despite all the other initiatives, that's the only driver working with Microdia webcams.

---

### Post by intel on 2008-01-27
**Microdia** 
(Webcam Support group for all Microdia chipsets under Linux)
Q) Is my webcam a "microdia"? 
A) Execute the following command 
    #lsusb
If you see any of the following numbers, you have a "microdia" webcam
0c45:6027, 0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:6242, 0c45:6253, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:62c0, 0c45:8105
(basically 0c45:<xxxy> above is enough to conclude you have a microdia webcam) 

All of the above webcams are unsupported under Linux


[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

 
Please join this Group, to help each other get better support for these webcams from Linux.

---

