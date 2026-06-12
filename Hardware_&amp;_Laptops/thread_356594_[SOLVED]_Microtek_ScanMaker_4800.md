---
title: "[SOLVED] Microtek ScanMaker 4800"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by alienexplorers on 2007-02-08
I own a Microtek Scanmaker 4800 that I have running partially under Ubuntu.  It scans in B&W correctly, but if I scan in color it distorts the scan to the point it is unusable.  I know that this scanner is supported under Sane so it should work.  Is there anyone with information on how to get color scans to work correctly.  I normally run under 300dpi to keep the scans small.

---

### Post by woland on 2007-02-09
Same problem here...

BTW, next time DON'T BUY Microtek. These bastards, for quite a long time, were demanding money for downloading drivers from their web site.
When I've contacted them, they have replied that: "It is our company's policy."

---

### Post by george3095 on 2007-12-28
I ALSO have a ScanMaker 4800 and a no-doubt related problem: When starting XSANE and it scans for peripherals, it "seems" to find the scanner. But, when I command it to scan, I get a message that (not THE exact message) to the effect that I don't have rights or permissions to connect to the scanner. Please let me know what you (alienexplorers) have done to EVEN get to access the scanner. I cannot get there.

---

### Post by fredsea on 2008-02-18
Seems familiar. I installed Gutsy on a desktop that used to run Mepis 6.5 (which was Dapper based anyway). My 4800 was easily recognized by Mepis (and color scans were horrible - using GIMP rather than Kooka in KDE made them better, though). When I did a liveCD test run of PC Linux OS it saw the scanner right away too.

Now, under Gutsy, the scanner is recognized, is listed everywhere (e.g., it shows as "Bus 005 Device 008: ID 05da:30cf Microtek International, Inc. ScanMaker 4800" for lsusb), but any attempt to launch xsane returns a nasty "Failed to open device `sm3840:libusb:005:008': Access to resource has been denied." This, regardless of starting xsane as root (sudo) or not. Attempts to chmod stuff (/proc/bus/usb is empty, but there is a file /proc/bus/pci/05/08.0) didn't change anything either...

It's less than life threatening, but it is very annoying... Suggestions? :confused:
TIA!

---

### Post by peapodgrrl on 2008-04-20
I was wondering if somebody would be so kind to help me with my 4800 as well. I have disliked this scanner from day one; my husband bought it through our IT guy and for what we spent, we could have had a much superior product. But I am not here to whine about that :)

I make a few scans, and then inevitably, this message:

MICROTEK MSSTI.DLL  (USB)

Failed to read image!
System Error 0, the operation completed successfully.
BulkInbytes: 112704, returned bytes 9215

....and then the scanner software locks up, and I have to close everything and begin again. It does seem to happen with more frequency at higher PPI rates. I print images on tiles for a living, so I must have high res scans...and there is definitely a difference to my eyes between 1200PPI and 2400PPI.

Can somebody help me? I am really losing it. Thank you in advance. :)

Peapodgrrl

---

