---
title: "Fixed minolta 2300dl by installing foo2zjs"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by Simon-au on 2005-09-18
Hello Ubuntu world.
Have got my Minolta 2300DL printing on AMD64 5.11 Breezy  and
Kbuntu 5.04.

1. install foo2zjs

2. Download latest PPD file from
[http://www.linuxprinting.org/show_printer.cgi?recnum=Minolta-magicolor_2300_DL](http://www.linuxprinting.org/show_printer.cgi?recnum=Minolta-magicolor_2300_DL)

3. Setup via desktop printer utility interface to cups.

3a. My **Gnome setup** 5.11 
Gnome System->Administration->Printing 

Setup printer as Network HP Jet Direct/(TCP on KDE) - Do Not use IPP or HTTP.

set Host:  printer ip address.
Set port:  9100

On next page click on Install Driver and install previously downloaded driver or 
select from list if it is allready installed.

Edit properties of printer to set to A4 and colour printing etc...

3b.My **KDE** 5.04 
KDE - Utilities->Print Manager

Use the Add Printer/Class option
Setup printer as Network printer (TCP) - Do Not use (IPP/HTTP).
Printer address: printers ip address.
Set port: 9100
Next>
Printer Model Selection:
Use the other button to load downloaded driver PPD file.
Next>
Use setting to adjust paper, duplex, colour etc..
click Next untill you need to add printer name, then finish.


Thanks to the Ubuntu people.

hope this help someone or maybe me the next time I need to do it.

Simon

---

### Post by bhtooefr on 2007-03-28
I know this is gonna be a necropost, but...

**THANK YOU!**

Worked on Edgy just fine - I had previously installed the official Konica Minolta Magicolor 2430DL drivers, though, and used those instead. Over USB, the foo2zjs drivers were giving me greyscale, so I used the 2430DL drivers (which will work on a 2300DL with no changes) instead.

I had tried to use IPP, but all that was doing was giving me headaches by crashing the printer. (Keep in mind, on Windows, the thing's fine with IPP.)

---

