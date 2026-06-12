---
title: "CUPS not behaving, help!!"
date: 2009-06-23
forum: Hardware
---

### Post by Camilia on 2009-06-23
I recently swithched color cartridge for black cartridge in my printer hp deskjet 3930v. For it was very low and black cartridge is cheaper. Printing result is a blank page. When I do a print test in HPLIP the page prints. In CUPS the print test result is a blank page. I change the printout mode to black cartridge and get page done. Click out and click back in and see the the setting is back to color cartridge. 

I unpluged the printer and tried uninstalling printer in CUPS and it didn't do it. 

Follow the instruction in ubuntupocketguide-v1-1.pdf to get printer to work.     print a test page in Ubuntu 8.10, open the Printer Configuration
window (System > Administration > Printing), then double-click the printer&#8217;s icon and click the PRINT TEST PAGE button. Blank page printed. Then click on the print options and change the print out mode to black cartridge. Result was printed page. I guess I was wrong about CUPS malfunctioning.


Tried adding printer as another printer for CUPS has it listed as hp deskjet 3900.

The simple thing to do would be to buy a color cartridge but I have already bought 2 black cartridges. Also I am unemployed at present thus really can't afford to buy another cartridge.

In terminal did a check. These pasted concern me.
sudo hp-check -r
HPOJ running?

No, HPOJ is not running (OK).

Checking for CUPS...

Status: scheduler is running

error: Version: (Not available. CUPS may not be installed or not running.)


cups11-build=no

shadow-build=no


foomatic-ppd-install=no


foomatic-rip-hplip-install=no

restricted-build=no


qt3=no

qt4=yes

printer_name = Deskjet-3900

device_uri = hp:/usb/Deskjet_3900?serial=CN5CM1M2WY04DF

Device URI: hp:/usb/Deskjet_3900?serial=CN5CM1M2WY04DF

error: 1 error or warning.

---

