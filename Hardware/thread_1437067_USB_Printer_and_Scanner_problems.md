---
title: "USB Printer and Scanner problems"
date: 2010-03-23
forum: Hardware
---

### Post by pernest on 2010-03-23
Hi

I'm having fun with an old printer and scanner. Whatever the problem is, it seems to manifest itself differently every time. Unfortunately I need to ask for help with the diagnosis as I am unfamiliar with linux.

I have a usb scanner,  Benq/Acer Scan to Web 4300 (listed as supported by sane). With an 'out the box' install of ubuntu onto a fresh hard disk, the scanner was detected and worked with no problems.

The printer is a HP Deskjet 690c. Because it connect via the parallel port and my new motherboard doesn't have a back panel parallel port connector I couldn't connect this printer straight away, but had to to order a usb to parallel converter. When I plugged I plugged the printer in, it worked fine.

The problem started when I tried to scan again, after the printer had been successfully connected. When I tried to use xsane GUI, I was getting the following error:

   Failed to open device `snapscan:libusb:006:003': Invalid argument.

and running xsane from command line gave the more informative:

   Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin

After a bit of reading I put the copied the correct firmware to the computer and pointed snapscan.conf to it. Got some other errors which I cant quite remember (something like "no scanner found"). But after unplugging and replugging the scanners usb cable it started working again.

However with the scanner working the printer was now acting oddly. Trying to print just a plain text document, the job went to the print queue and then disappeared (as though it had been sent to the printer) but nothing came out of the printer. When I unplugged the usb to parallel cable and plugged it in again, the printer printed out the document I wanted it to.

After some plugging and replugging I have both the printer and scanner working together (I'm able to scan to print). However when I restart the computer I'm faced with the need to randomly plug and replug before things work properly.

The scanner seems to be working relatively consistently from start up at the moment, but the printer definitely needs to be replugged before it will work.

I'm using karmic 9.10 and my motherboard is an ASUS M4A785T-M.

If anyone can suggest any diagnostic tests I will run them and post the results. Any help will be very gratefully received.

---

### Post by pernest on 2010-03-24
Hi

Sorry to push this backup, but I was hoping that someone might be able to offer some help.

---

