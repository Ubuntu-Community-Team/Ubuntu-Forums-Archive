---
title: "Star TSP 700II Thermal Receipt Printer"
date: 2014-04-28
forum: Hardware
---

### Post by ck234 on 2014-04-28
Hello,
    I am having trouble getting the star TSP 700II ethernet thermal receipt printer to work properly with ubuntu server.

I installed the drivers from the Star website.

I added the printer in cups as a lpd printer - withe the format lpd://x.x.x.x./printername (IP address /name I made up for the printer) and I set the paper width to 70x30mm as instructed in the Star guidance document.

The printer will print a test page, but will not autocut, and then hangs for a longtime "spooling".  It is then not possible to print a further page.

Any suggestions appreciated.  Thank you.

---

### Post by ck234 on 2014-04-30
OK - so I got this to work.  The problem seemed to be that the printer was expecting a media size of label, but I was loading 80mm receipt roll  into it .  From reading the hardware manual, you have to tell the printer to expect 80mm paper using a "memory switch".  This is a software switch.  To access this I installed the Star printer utility on a Windows XP machine and set the paper "printable area" to 80mm.  This sorted the printer out, it works fine now.

---

