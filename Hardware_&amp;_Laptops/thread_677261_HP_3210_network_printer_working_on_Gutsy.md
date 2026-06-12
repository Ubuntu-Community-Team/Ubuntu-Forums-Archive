---
title: "HP 3210 network printer working on Gutsy"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by Marco_Polo on 2008-01-24
Just a quick review of how I successfully configured the HP 3210 All-in-one to run over my network.  Thanks to the writers of many posts who convinced me the installation would go smoothly.

First, powered it on, installed the inkjets and printed a test page - so far so good.
Next, plugged connected it to my router and checked with a browser for LAN clients at [http://192.168.0.1/lan.htm](http://192.168.0.1/lan.htm) (it's a D-Link router.)  The printer had an IP assigned and a hard-to-remember hostname.

Logging into the printer directly at [http://hostname.local](http://hostname.local) allowed me to assign a new name: "HP3210" and view ink levels.
I configured the printer through the CUPS pages at: [http://localhost:631/](http://localhost:631/) although I'm aware it can also be done through Gnome under System->Admin->Printing.  In the CUPS pages I used:
Administration->Add Printer
Enter Name, location and description on first page.
Enter Device: HP Printer (HPLIP) on second page.
Enter Device URL: socket://HP3210.local:9100 on third page - the documentation at localhost:631/help/network.html led me to this setting as the printer does not support IPP.
The Printers tab on the CUPS pages allowed me to successfully print a test page.
$> 'lpstat -a' lists it as an available printer
Setting my LPDEST environment variable to the hostname - HP3210, set the printer as the default and the lp and lpr commands work: $> 'lp filename' $> 'lpr -P HP3210 filename' and I even get the printer icon popping up on the toolbar to manage print jobs.  Great.

As a side note, the print quality looks good enough for home use, and the scan and copy functions seem to work well, also.

Hope this may help someone ...

---

