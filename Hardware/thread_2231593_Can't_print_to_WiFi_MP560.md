---
title: "Can't print to WiFi MP560"
date: 2014-06-26
forum: Hardware
---

### Post by cbmckinney on 2014-06-26
I just installed 64bit Ubuntu 14.04 LTS alonside Windows 7 on my Toshiba Satellite A660 laptop (downloaded yesterday, 6/25/14).

I added the PPA [http://ppa.launchpad.net/michael-gruz/canon-trunk/ubuntu](http://ppa.launchpad.net/michael-gruz/canon-trunk/ubuntu) to the Ubuntu Software Center.

I was able to add my Canon Pixma MP560 printer. The Device URI shows as cnijnet:/00-1E-8F-CD-D4-5C, and the Make and Model show as Canon MP560 series - CUPS+Gutenprint v5.2.10-pre2.

When I hit the Print Test Page button, everything seems to go fine--except nothing prints. When I check the queue, I find my document is being "held," and when I hit the Release button, it momentarily goes to "printing" but then quickly reverts to "held." After enough time, trying to release the document aborts the print job. This behavior is the same whether I select Canon - MP560 or Canon - Pixma MP560 driver.

What am I missing?

---

### Post by pdc on 2014-06-26
> I added the PPA [http://ppa.launchpad.net/michael-gru...n-trunk/ubuntu](http://ppa.launchpad.net/michael-gru...n-trunk/ubuntu) to the Ubuntu Software Center. ......that would be so you can use the linux drivers that Canon supply; 

..........however you need to go ahead and install them...........

_______________________

> the Make and Model show as Canon MP560 series - CUPS+Gutenprint v5.2.10-pre2. so you only have the open-source gutenprint installed; many are very happy with gutenprint;

_______________

Canon only seemed to supply a 32bit driver in 2008 when they released the MP560; (that was mainly what was used then); 

_________

here is an ubuntu wiki [https://wiki.ubuntu.com/DebuggingPrintingProblems#Network_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Network_printer) that you might like to work through;

---

### Post by hatch_jd on 2014-07-19
Following this thread - with the same problem I realised that what I needed to do was select the other printer driver option (installed from the PPA).

Not the default Canon MP560 which is auto-selected when the printer is found and gives you the CUPS+Gutenprint v5.2.10-pre2 open source drives,
but instead choose Canon MP560 Ver.3.90 which presumably gives you Canon drivers from the michael-grunz PPA.

If you don't see this alternative then follow the instructions here [http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mp-series-on-ubuntu-14-04-trusty-tahr-linux-mint-17-qiana-and-their-derivative-systems/](http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mp-series-on-ubuntu-14-04-trusty-tahr-linux-mint-17-qiana-and-their-derivative-systems/) to install the Canon drivers from the PPA.

Having edited Printer Properties to chosen the 3.90 driver instead of the default, I released the existing Held print job in the queue and it printed.

---

