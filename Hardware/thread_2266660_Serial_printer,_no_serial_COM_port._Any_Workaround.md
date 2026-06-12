---
title: "Serial printer, no serial COM port. Any Workaround?"
date: 2015-02-24
forum: Hardware
---

### Post by 681726-0 on 2015-02-24
Hi all,  I'm trying to connect a printer (Epson TM-T88IV) to my lubuntu laptop. The problem is that the printer comes with serial interface (RS-232), but the laptop doesn't have any port for it. I've downloaded and installed the lastest linux driver from [https://download.epson-biz.com/modules/pos/index.php?page=prod&pcat=3&pid=30](https://download.epson-biz.com/modules/pos/index.php?page=prod&pcat=3&pid=30) No matter how can connect the cables, I just can't find the printer on cups set-up page.  Here are the list of equipments I have: 1. [Cable] Serial (more pins matching the printer) ------------- Serial (less pins) 2. [Cable] Serial (less pins) --------------- Ethernet(RJ45?) 3. Modem+Router: 4 x RJ45-type ports. 4. Laptop: 2 x USB ports, 1 x Ethernet port, 1 x VGA port  I have absolutely no clue about what should I do next. Please help me.

---

### Post by tgalati4 on 2015-02-24
You can buy a USB-to-serial adapter or some computers have a dock that has a serial port in the back.  Otherwise, it might be easier to find a newer, USB printer.

---

### Post by 681726-0 on 2015-02-25
Is it not possible to use the existing materials that I have to run the printer on local network?

And with the USB-------Serial, does it turn the printer into USB device? I'm asking it because the manual indicates different procedures for configuring USB model and serial model.

---

### Post by coldraven on 2015-02-25
> And with the USB-------Serial, does it turn the printer into USB device?
AFAIK you would still use the Serial config but choose /dev/ttyUSB0 as the port rather than COM1 or COM2.
The adapters cost £2 on eBay
[http://www.ebay.co.uk/itm/USB-2-0-Male-to-RS232-Serial-DB9-9-Pin-Adapter-Cable-PC-Brand-NEW-/271349531073?pt=LH_DefaultDomain_3&hash=item3f2db141c1](http://www.ebay.co.uk/itm/USB-2-0-Male-to-RS232-Serial-DB9-9-Pin-Adapter-Cable-PC-Brand-NEW-/271349531073?pt=LH_DefaultDomain_3&hash=item3f2db141c1)

---

### Post by 681726-0 on 2015-02-25
Thank you tgalati4 and coldraven for your great advice. Will try the cable when it arrives.

---

### Post by tgalati4 on 2015-02-25
Let us know how it works out.  

Some printers have problems with USB-to-serial adapters, but you have to try it to find out.  The symptoms would be stopping in the middle of a print job, or errors in the print out--dropouts, random characters, etc.  Serial communication is syncronous--requiring a continuous connection.  USB is a hotplug/asyncronous communication.  The adapters work in 90% of the cases, but some equipment is sensitive and will only work with a "real" serial port.

---

