---
title: "Looking for low-cost printer/scanner compatible with Ubuntu 12.04"
date: 2013-06-26
forum: Hardware
---

### Post by cigtoxdoc on 2013-06-26
I need to replace my ancient Epson CX 4800.  I need letter-size printing and scanning.  Looking for something I can find at office stores, Best Buy, etc., and will work with Ubuntu 12.04 with minimal hassles.

Thank you,

John

---

### Post by TheFu on 2013-06-26
I use a Samsung 1740 laser printer and Brother 240C All-in-One with Linux.  The All-in-One doesn't print, because the ink is too, damn, expensive, but we use everything else on that device a lot.  I'm a huge believer in printing with a laser to save money. Toner lasts many years, where as ink seemed to dry out annually ... just before tax printing time, so $40 in replacement ink was needed every year, even if we only printed 20 pages the rest of the year.

It has been 4 yrs since I changed the toner on that $55 Samsung laser.  Got Mom a brother laser printer 3 yrs ago, she's on the same toner cartridge and prints 100 pgs a week, easy. She likes to read email on paper.  She had a Canon, but I was unable to find non-commercial drivers for it. The cost of the drivers was the same as the Brother Laser printer, so we gave the Canon away to a college student and spent the money to help a company that is more Linux friendly.  Sorry, don't remember which model Mom has ... let me remote into her machine ... Brother HL-2140.  Not an all-in-one, but still we've been happy.

---

### Post by pdc on 2013-06-26
We have a Canon MG3100 series printer; it offers duplex, wireless; scanning; we also have a Canon MG2100; the latter can be found for $US40 at times I suspect; both work well;

Canon provide drivers [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal) for the printing side and the scanning side

Brother provide drivers for their similar range of MF devices (multi-function);

---

### Post by papibe on 2013-06-26
Hi cigtoxdoc.

I've had very good experiences with low budget HP All-in-one printers (printer/scanner/copier). Both have been in the $60-$80 range.

Regards.

---

### Post by TheFu on 2013-06-26
> **pdc said:**
> Canon provide drivers [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal) for the printing side and the scanning side

Definitely look for the driver **before** you buy.  I just looked for a Linux driver for Canon printer Mom had again and didn't find it.  I've seen responses in other threads that pointed to different websites in regions of the world to get the Linux drivers, but never on the USA driver website.  I'm not saying that Canon doesn't make fantastic printers - the output under Windows was always fantastic, but if you don't run Windows ... er .

The Samsung printer listed above "just worked." No special drivers to be downloaded.  That is my preference for all Linux hardware choices.  I've been burned by printers, network cards, wifi, bluetooth, disk controllers, and webcams enough.  The "just works" part is so much easier and more likely to work when 16.04 is released.  I think the brother all-in-one needed scanner drivers and I had to manually tweak the group permissions so that SANE could be used by anyone.   BTWm **gscan2pdf** rocks.

There is a **Linux Printing Hardware Guide** somewhere. I think they spend a bunch of time maintaining it.

---

### Post by Cheesemill on 2013-06-27
I recently picked up an HP 2510 all-in-one on sale for £25.

Just plugged it in and everything worked, all of the drivers were already installed (as part of the hplip package).
I did know this was going to be the case before I bought it though as I'd checked for Linux support on the HP website ***before*** purchasing.

HP have always been good for Linux compatible hardware, you can check the supoorted devices here...
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by jp734 on 2013-06-27
I am not a big fan of all-in-ones, nor a fan of inkjet printers as well. I agree with TheFu as far as laser printers. 

So we have Dell 1700n laser printer (network printer - has an ethernet connection). It works pretty well and never had any problem. It uses Lexmark Optra E321 driver. 

For a scanner, we have an old Acer Prisa 620u usb flatbed scanner. Can scan legal size copies. Setup is very easy as well. All I had to do is edit /etc/sane.d/snapscan.conf and to tell it where the firmware for my scanner is. Been using this scanner for yeeeeaaaaarrrrrssss and still going. Since it's old, you can probably get it for CHEAP!

I just checked ebay for the heck of it. Scanner Acer Prisa 320u for $6.00 :D - TALKING ABOUT GREAT DEAL!!!

---

### Post by jp734 on 2013-06-27
I am not a big fan of all-in-ones, nor a fan of inkjet printers as well. I agree with TheFu as far as laser printers. 

So we have Dell 1700n laser printer (network printer - has an ethernet connection). It works pretty well and never had any problem. It uses Lexmark Optra E321 driver. 

For a scanner, we have an old Acer Prisa 620u usb flatbed scanner. Can scan legal size copies. Setup is very easy as well. All I had to do is edit /etc/sane.d/snapscan.conf and to tell it where the firmware for my scanner is. Been using this scanner for yeeeeaaaaarrrrrssss and still going. Since it's old, you can probably get it for CHEAP!

---

### Post by kurt18947 on 2013-06-27
I go along with Brother.  Installation may not be quite as convenient as HP but it's not bad, especially using Brother's script to install printers.  I think Brother ink is a little more reasonable than HP.  There are also refillable cartridges available.  I've had decent luck with these guys:
[http://www.inkowl.com/index.php?B=1](http://www.inkowl.com/index.php?B=1)
One thing to remember with inkjets, especially those that have printheads separate from the ink cartridge - print something once a week even if it's a test page.  Inkjet heads can plug if they sit unused too long and if cleaning doesn't work, repair will probably cost more than a new printer.  A plus for HP is that some of their printers (not all) have printheads built into the ink cartridge.  If you have printhead issues, just replace the cartridge.   This is not an issue with lasers but if you need color, lasers get a little expen$ive.

---

### Post by cigtoxdoc on 2013-06-28
Thank you for your suggestions.  I had to take care of immediate need in my backup office (have a place to go about 350 miles from my main office with its Brother MFC-9440CNs).  Local Sam's Club had hp OfficeJet 6700 Premium.  Yes, after installing the latest version of hplip from SourceForge, I have a working system both printing and scanning.  PC is an ancient but very well running hp Pavilion a600n.

John

---

