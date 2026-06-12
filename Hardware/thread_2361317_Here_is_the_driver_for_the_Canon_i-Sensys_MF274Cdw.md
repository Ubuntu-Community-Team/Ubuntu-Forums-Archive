---
title: "Here is the driver for the Canon i-Sensys MF274Cdw printer"
date: 2017-05-15
forum: Hardware
---

### Post by lozowy-gmail on 2017-05-15
I've uploaded the specific printer driver file for the **Canon i-Sensys MF274C** printer to the cloud. It can be downloaded from here:
*link removed*

This is a .ppd file, which should be copied to the following directory:
/etc/cups/ppd/

Thereafter simply use the command "Add" from System Seetings -> Printers
and this specific printer should be visible and installable.

On how to install CUPS, see: [https://help.ubuntu.com/lts/serverguide/cups.html](https://help.ubuntu.com/lts/serverguide/cups.html)

_ _ _ _ _ 
After lots of fits and starts I somehow found/extracted this specific printer driver. Could not replicate how I got a hold of it, though, so I'm putting it out there for everyone else. ;)

---

### Post by vasa1 on 2017-05-15
The link to the driver has been removed. Please provide a link from Canon itself.

---

### Post by pdc on 2017-05-16
I can't find a reference to the MF274Cdw .. I can't see that it exists ...... whereas the MF724Cdw does ........ 

and perhaps best to get a driver from the Canon Europe website [http://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/laser/laserbase_mf_series/i-sensys_mf724cdw.aspx?type=drivers&language=&os=Linux%20(64-bit)](http://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/laser/laserbase_mf_series/i-sensys_mf724cdw.aspx?type=drivers&language=&os=Linux%20(64-bit))

It is not too hard and either the Canon Europe or Canon UK will be pleased to help: rpm and deb packages are provided; in 32 and 64bit formats; and an install script does all the work; driver install; printer registration;

It is the Linux_UFRII_PrinterDriver_V331_uk_EN.tar.gz                     ............... there is an install script ........

so commands are: 
cd Downloads
tar -zxvf Linux_UFRII_PrinterDriver_V331_uk_EN.tar.gz
cd Linux_UFRII_PrinterDriver_V331_uk_EN
./install.sh

---

