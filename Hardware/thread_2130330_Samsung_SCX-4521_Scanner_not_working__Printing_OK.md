---
title: "Samsung SCX-4521 Scanner not working / Printing OK"
date: 2013-03-29
forum: Hardware
---

### Post by sknagesh on 2013-03-29
Hi

I have connected Samsung SCX-4521F Printer/Scanner to Ubuntu  12.04 machine via USB. First using CUPS I was able to print to this  printer both locally and over network with out any problem. Afterwards I  wanted to use the scanner functionality of this device. So I googled  and found some directions to install Samsung Unified Linux Driver using  apt-get method.  Using these instructions I installer the driver for  this device.

Now when I run Configurator both as as user and as  root I can configure the printer, but I Can not configure the scanner  even though it is listed under scanner page as connected to USB:0. 

scanimage -L finds the scanner correctly, but xscan errors out with device i/o  error. I can not scan any thing.

In syslog the error message is "xsane: io/hpmud/pp.c 627: unable to read device-id ret=-1"

Can any one help me solve this issue.

Please let me know if you need any more information.

Regards

SKN

---

