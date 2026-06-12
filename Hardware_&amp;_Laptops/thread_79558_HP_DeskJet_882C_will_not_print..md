---
title: "HP DeskJet 882C will not print."
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by MkIII_Supra on 2005-10-20
I have been searching but have yet to find an answer that works. I have a USB HP DeskJet 882C color printer with the latest driver off of this site: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_882C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_882C)

When I use the KDE printer set-up I am shown 16 USB options but I only have 2 USB ports. I have tried all options available with no success. I hooked the printer to my SuSE box and it works, I then hooked it to Win2K and of course it works, so I tried PCBSD and with a litte effort... it works. But on my Ubuntu 5.04 with KDE installed it doesn't work.

Below are my system specs and print.conf. I am stumped and stuck.

Toshiba Satelite A15-S129
Intel Mobile Celeron 2.4GHz
512MB RAM
Ubuntu 5.04 kernel v. 2.6.10-5-386
KDE 3.4

# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Thu Oct 20 09:49:11 2005
<Printer HPDJ882c>
Info HP DeskJet 882C
Location My Cubicle
DeviceURI usb:/dev/usb/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
<DefaultPrinter Laptop>
Info Raw printer
Location roving
DeviceURI ipp://192.168.0.10:631/printers/HPBIJ1100
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

Thank you.

---

### Post by David Haas on 2005-10-21
Hi Mklll_Supra--Ubuntu Hoary contains 4 drivers (PPD files) for the HP Deskjet 882C. So, by selecting one of these, the chances are high that your printer will work fine. Sometimes one driver works better than another. Because these drivers come with Hoary, I'd use these first. The drivers are : 
HP-DeskJet_882C-cdj850.ppd.gz
HP-DeskJet_882C-cdj880.ppd.gz
HP-DeskJet_882C-hpijs.ppd.gz
HP-DeskJet_882C-pcl3.ppd.gz.

They are located in the HP directory at /usr/share/cups/model/foomatic-ppds/HP.

I'm running Gnome, so I'm not familiar with the KDE printer manager, but it must ask you to first select your printer from a list and then select the driver (PPD file). To find the drivers above, you'll need to click through the directories noted above.

One other (odd) thing. sometimes the printer needs to be on before booting up the computer--but I don't need this for my HP Deskjet 5740.

I hope this note helps.

David 

.

---

