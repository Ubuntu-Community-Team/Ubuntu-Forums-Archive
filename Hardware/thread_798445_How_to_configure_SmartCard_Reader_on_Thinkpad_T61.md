---
title: "How to configure SmartCard Reader on Thinkpad T61"
date: 2008-05-18
forum: Hardware
---

### Post by arroba3 on 2008-05-18
Hi everybody!

I have a Thinkpad T61 laptop, with an integrated SmartCard reader and I am running with Ubuntu 8.04. The thing is that I have been searching how to configure the reader, but I found nothing. Could someone help me?

Thank you!

Arroba3.

---

### Post by vussvillem on 2008-07-09
First you have to tell us what is the model of your Smart Card reader. To do that, execute in terminal: lspci (find it out, or if you're confused post the output in here).

Meanwhile, drivers and other additional packages for Smartcard readers can be found 
[http://pcsclite.alioth.debian.org/ccid.html](http://pcsclite.alioth.debian.org/ccid.html)
[https://gna.org/projects/o2scr](https://gna.org/projects/o2scr)

---

### Post by greenvirag on 2009-01-07
I have the same thinkpad. Some remarks:

there can be found in an t61 the following smart card reader: Lenovo Integrated Smart Card Reader. This device is working on usb connections, so lspci will not list it. Use lsusb.

If you get a similar line in the output:
Bus 005 Device 002: ID 17ef:1003 Lenovo
then ok, you found your reader.

The provided driver for it is ccid:
sudo apt-get install libccid

---

