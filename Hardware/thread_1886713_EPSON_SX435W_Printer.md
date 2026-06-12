---
title: "EPSON SX435W Printer"
date: 2011-11-25
forum: Hardware
---

### Post by cygnusnsf on 2011-11-25
Hi All, HELP! just installed this new printer and bosh works great in Smindows 7 but I can for the life of me cant get it working in Ubuntu 10.04 LTS.

Although it does appear to pick up the printer there does not appear to be a driver for the SX435 only SX415 but then this does not appear to work correctly.

I guess either I have to update something or get a driver but cant find it or anything to help.

For info - using 10.04 LTS as its the only one supported for work at present.

Hope some kind soul can help.
Rgds
Cygnus

---

### Post by cygnusnsf on 2011-11-26
Just to say thanks to all who looked but I at last got it to work....
Works out of the box with ubuntu 11.10 btw but can install the drivers from url below and this then works and detects the printer without issue.

linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-i386/epson-inkjet-printer-escpr_1.1.0-1lsb3.2_i386.deb

Rgds
Cygnus

---

### Post by Comodín on 2012-10-06
Did any of you get the scanner to work (USB or wireless)?!?

---

### Post by lukybuehl on 2013-05-08
I did get the scanner work. I installed the driver on Lenovo 3000 N200 under Ubuntu 12.04 LTS.

I downloaded the drivers from:
[http://download.ebz.epson.net/dsc/search/01/search/](http://download.ebz.epson.net/dsc/search/01/search/)
There was no specific driver for sx435w, but I downloaded the driver for sx430 and it works.

After the download, you have to install the drivers step by step
1. iscan-data_1.22.0-1_all.deb
2. iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb
3. iscan-network-nt_1.1.0-2_amd64.deb    (Optional if you want to scan via ethernet or Wi-Fi)
I hope it can also work on your device

---

