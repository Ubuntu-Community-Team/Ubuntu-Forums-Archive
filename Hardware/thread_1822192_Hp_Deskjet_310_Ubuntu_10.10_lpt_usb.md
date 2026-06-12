---
title: "Hp Deskjet 310 Ubuntu 10.10 lpt usb"
date: 2011-08-10
forum: Hardware
---

### Post by lborka on 2011-08-10
Hi All!

  I am trying to connect to my asus eee pc 1001px with a HP Deskjet 310 printer. My netbook does not have a LPT port, so I'm using a LPT to USB converter cable. Printer is not recognized. Please bear in mind I'm not an advanced Ubuntu user. Does anyone have a solution? Thank you in advance.



lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5119 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by nomko on 2011-08-10
Just checked the site of CUPS and your printer wasn't mentioned on that site. And on the HPLIP driver site your printer can't be found either, only the HP Deskjet F310 All-in-one. You're sure it is a Deskjet 310 (just to check)?

---

### Post by lborka on 2011-08-10
Hi nomko.

Thank you for the fast reply. Meanwhile I have found a site, wich solved my problem: [http://blog.maestropublishing.com/usb-to-parallel-converter-trendnet-tu-p1284-o](http://blog.maestropublishing.com/usb-to-parallel-converter-trendnet-tu-p1284-o)

At the "Enter device URI" I have entered "parallel:/dev/usblp0" and I could select my printer from the list, exactly as the site mentions, and I was able to print a test page. 

Problem Solved!

---

### Post by nomko on 2011-08-10
Nice to see you fixed it yourself!
 
Haven't though about the adaptor myself since most problems are driver related.

---

### Post by billstei on 2011-10-18
I did a fresh install of Ubuntu 11.10 and I also have the Prolific Technology, Inc. PL2305 Parallel Port, which is listed when doing lsusb, but there is no /dev/usb/lp0 or /dev/usblp0.  This was working in Ubuntu 11.04, and the hardware has not been changed.

Edit: I added "usblp" (without the quotes) to the file /etc/modules, used parallel:/dev/usblp0 as the URI in the Add Printer dialog, selected the driver manually from the printer driver list, and it is working now.

---

