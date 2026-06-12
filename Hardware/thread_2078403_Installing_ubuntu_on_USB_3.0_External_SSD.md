---
title: "Installing ubuntu on USB 3.0 External SSD"
date: 2012-10-30
forum: Hardware
---

### Post by TheSparko on 2012-10-30
As we know, Solid state drives are much quicker compared to normal HDDS when it comes to transer of data.

If i were to install a ubuntu on a usb 3.0 External ssd, then boot it from my boot menu in my bios, would I be able to take advantage of the fast speeds that SSD can provide?

I mean, the SSD is connected through the usb 3.0 connection - which is a minor bottleneck - but in theory, i should be able to get significantly greater speeds then if i were to install it on my HDD?

---

### Post by oldfred on 2012-10-31
Depending on SATA2 or SATA3 hard drive will be faster. And some discuss theory and others mention a more practical number so I do not have total consistency in my notes.

SATA II - 3.0 Gbit/s
SATA revision 3.0 (SATA 6 Gbit/s)

Mb/s or MB/s? USB 2.0 tops out at 480Mbps, which is about 50MB/sec.

[http://en.wikipedia.org/wiki/USB2](http://en.wikipedia.org/wiki/USB2)
The theoretical maximum data rate in USB 2.0 is 480 Mbit/s (60 MB/s) per controller
[http://en.wikipedia.org/wiki/USB3#USB_3.0](http://en.wikipedia.org/wiki/USB3#USB_3.0)
SuperSpeed (USB 3.0) rate of 4800 Mbit/s (~572 MB/s).
But speeds are more limited by devices at each end.

My SSD is a low cost OEM version, I have seen newer ones rated twice mine.

SSD speed
fred@fred-Precise:~$ sudo hdparm -t /dev/sdd4
/dev/sdd4:
 Timing buffered disk reads: 626 MB in  3.01 seconds = 208.20 MB/sec
Older 160GB rotating drive:
/dev/sdb4:
 Timing buffered disk reads: 212 MB in  3.01 seconds =  70.46 MB/sec

---

