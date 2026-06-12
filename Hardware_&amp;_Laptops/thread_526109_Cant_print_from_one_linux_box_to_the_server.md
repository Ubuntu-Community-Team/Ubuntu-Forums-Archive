---
title: "Cant print from one linux box to the server"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by Gruelius on 2007-08-15
For some reason one of my FF pc's cant print to my FF server. My other one can so this might assist you

In the access log of the server i find
```
192.168.0.7 - - [15/Aug/2007:18:47:41 +1000] "POST /printers/KONICA_MINOLTA_magicolor_2400W_USB_1 HTTP/1.1" 200 360 Print-Job successful-ok
192.168.0.7 - - [15/Aug/2007:18:47:41 +1000] "POST /printers/KONICA_MINOLTA_magicolor_2400W_USB_1 HTTP/1.1" 200 265 Get-Job-Attributes successful-ok
192.168.0.7 - - [15/Aug/2007:18:47:51 +1000] "POST /printers/KONICA_MINOLTA_magicolor_2400W_USB_1 HTTP/1.1" 200 265 Get-Job-Attributes successful-ok
```

Nothing is in the error logs of either machines.

Thanks
Julius

---

### Post by Gruelius on 2007-08-16
D [16/Aug/2007:15:38:10 +1000] write_file: 8 file=11
D [16/Aug/2007:15:38:12 +1000] cupsdNetIFUpdate: "lo" = localhost...
D [16/Aug/2007:15:38:12 +1000] cupsdNetIFUpdate: "eth0" = 192.168.0.3...
D [16/Aug/2007:15:38:12 +1000] cupsdNetIFUpdate: "lo" = localhost...
D [16/Aug/2007:15:38:12 +1000] cupsdNetIFUpdate: "eth0" = fe80::218:f3ff:fe80:a03c%eth0...
D [16/Aug/2007:15:38:12 +1000] cupsdUpdateCUPSBrowse: Refused 221 bytes from 192.168.0.3

thats another lot

---

