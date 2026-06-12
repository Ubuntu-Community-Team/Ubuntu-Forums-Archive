---
title: "Printer configuration oddities in Kubuntu 13.10"
date: 2013-12-03
forum: Hardware
---

### Post by pwabrahams on 2013-12-03
I've finally gotten my printer configured correctly in Kubuntu 13.10, but it was a mighty struggle.  The printer is an ancient but quite serviceable HP LaserJet 5M with PostScript and a duplexer.  It has a network adapter plugged into the parallel port with IP address 192.168.0.11.   Here's what I discovered.

Some configuration settings that appear to be identical aren't.  When configuring the printer (via System Settings / Printers), two of the choices are "Manual URI" and "AppSocket/HP Jet Direct".  Whichever I choose, the configuration eventually shows up as "socket://192.168.0.11:9100", but the behavior is far from identical.  If I specify the configuration via "Manual URI", the printer doesn't respond to jobs; it stays in the Ready state.  If I use AppSocket (which fills in the 9100 automatically), the printer works correctly.  In either case I use the CUPS/Gutenprint driver.

If I attempt to provide an explicit PPD file with Manual URI, the file location of the PPD appears to be accepted.  However, when I click OK or Apply, the file location disappears and is replaced by the Foomatic / Postscript driver -- not even the CUPS driver.

Very early on I determined that the network was not responsible for my difficulties.  Throughout all my testing, I was able to ping the printer.  Furthermore, the web interface provided by the network adapter worked and was able to print a test page.

I'm posting this thread primarily because the information I found might be useful to others.  Explanations of what is going on would be very welcome, though I've already solved my operational problem -- for now, at least.

---

