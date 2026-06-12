---
title: "gnome not detecting printer"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by mmorton8 on 2005-05-18
I have a Brother HL-1440 that I cannot get detected under the Gnome printing setup tool.  When I do an lsusb it shows the printer there when connected but when I run the Gnome Printing setup tool, the use detected section is not selectable.  Are there issues between USB 1.x and 2.x ports?  Any help is appreciated.

cheers O:)

---

### Post by kamstrup on 2005-05-18
Can't you select a printer by specifying the port? Ie. ticking "Selct Printer by Specifying Port"-box and selectin the relevant usb port?

Try unplugging and re-plugging the printer and starting the install-tool again...

Good luck!

---

### Post by David Haas on 2005-05-18
In the printer GUI (System>Adminiustrating>Printing), what printer did you select? After selecting it, did you then select the PPD file for it--in the GUI? Your printer does seem to be supported by Ubuntu. I see that the PPD files for it are in the Brother directory at /usr/share/cups/model/foomatic-ppds/Brother. Three are listed: Brother-HL-1440-hl1250.ppd.gz; Brother-HL-1440-hpijs.ppd.gz; Brother-HL-1440-ljet4.ppd.gz. 
David

---

### Post by mmorton8 on 2005-05-19
[QUOTE=kamstrup]Can't you select a printer by specifying the port? Ie. ticking "Selct Printer by Specifying Port"-box and selectin the relevant usb port?

Try unplugging and re-plugging the printer and starting the install-tool again...

Good luck![/QUOTE]

I tried that and had no luck.  The other thing I haven't tried is to connect through the actual rear usb ports.  Maybe there is a difference.  There wasn't with Mandrake.

Thanks!    :)

---

### Post by mmorton8 on 2005-05-19
[QUOTE=David Haas]In the printer GUI (System>Adminiustrating>Printing), what printer did you select? After selecting it, did you then select the PPD file for it--in the GUI? Your printer does seem to be supported by Ubuntu. I see that the PPD files for it are in the Brother directory at /usr/share/cups/model/foomatic-ppds/Brother. Three are listed: Brother-HL-1440-hl1250.ppd.gz; Brother-HL-1440-hpijs.ppd.gz; Brother-HL-1440-ljet4.ppd.gz. 
David[/QUOTE]

I am pretty sure that the printer itself is supported, it worked fine under Mandrake. I think it is more me getting used to setting things up in Gnome rather than using a vendors tool like in RH or Mandrake.

---

### Post by mmorton8 on 2005-05-24
apparently the front USB ports are different and are not being scanned in the printer detection?  or I also had a USB hub plugged into the front which may have been conflicting perhaps.

Works great now though!  Thanks to those who tried to help! :)

---

