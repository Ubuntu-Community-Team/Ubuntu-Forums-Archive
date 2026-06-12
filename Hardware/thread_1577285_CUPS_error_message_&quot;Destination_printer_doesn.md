---
title: "CUPS error message: &quot;Destination printer doesn't exist&quot;"
date: 2010-09-18
forum: Hardware
---

### Post by derwisch on 2010-09-18
I have purchased a new printer of the make Brother HL-3040CN. I installed the lpr and cups drivers as model specific *.deb packages from the Brother homepage. The printer is connected over a LAN cable and a switch.

After the printer is found in the network and configured with help of CUPS (using the downloaded printer driver), I try to print out a test page, but to no avail. Instead the error message as given in the title (or rather: "Zieldrucker existiert nicht", which is the same in .de locale) is displayed.

These are the lines in the error log of CUPS:

D [18/Sep/2010:21:36:25 +0200] [Job 499] Read 8192 bytes of print data...                                              
D [18/Sep/2010:21:36:25 +0200] [Job 499] Wrote 8192 bytes of print data...                                             
D [18/Sep/2010:21:36:25 +0200] [Job 499] Read 8192 bytes of print data...                                              
D [18/Sep/2010:21:36:25 +0200] [Job 499] Wrote 8192 bytes of print data...                                             
D [18/Sep/2010:21:36:25 +0200] [Job 499] Read 5 bytes of print data...
D [18/Sep/2010:21:36:25 +0200] [Job 499] Wrote 5 bytes of print data...
D [18/Sep/2010:21:36:25 +0200] [Job 499] The printer is ready to print.
D [18/Sep/2010:21:36:25 +0200] [Job 499] Read 53 bytes of print data...
D [18/Sep/2010:21:36:25 +0200] [Job 499] Wrote 53 bytes of print data...
D [18/Sep/2010:21:36:25 +0200] [Job 499] 1 files to send in job...
D [18/Sep/2010:21:36:25 +0200] [Job 499] STATE: +connecting-to-device
D [18/Sep/2010:21:36:25 +0200] [Job 499] Connecting to 192.168.1.104:631
D [18/Sep/2010:21:36:25 +0200] [Job 499] Mit Drucker verbinden &#8230;
D [18/Sep/2010:21:36:25 +0200] [Job 499] STATE: -connecting-to-device
D [18/Sep/2010:21:36:25 +0200] [Job 499] Mit Drucker verbunden &#8230;
D [18/Sep/2010:21:36:25 +0200] [Job 499] Connected to 192.168.1.104:631 (IPv4)...
D [18/Sep/2010:21:36:25 +0200] [Job 499] prtMarkerSuppliesLevel.1.1 = -3
D [18/Sep/2010:21:36:25 +0200] [Job 499] prtMarkerSuppliesLevel.1.2 = -3
D [18/Sep/2010:21:36:25 +0200] [Job 499] prtMarkerSuppliesLevel.1.3 = -3
D [18/Sep/2010:21:36:25 +0200] [Job 499] prtMarkerSuppliesLevel.1.4 = -3
D [18/Sep/2010:21:36:25 +0200] [Job 499] prtMarkerSuppliesLevel.1.5 = -3
D [18/Sep/2010:21:36:25 +0200] [Job 499] prtMarkerSuppliesLevel.1.6 = 49969
D [18/Sep/2010:21:36:25 +0200] [Job 499] prtMarkerSuppliesLevel.1.7 = 14989
D [18/Sep/2010:21:36:25 +0200] [Job 499] prtMarkerSuppliesLevel.1.8 = 14989
D [18/Sep/2010:21:36:25 +0200] [Job 499] prtMarkerSuppliesLevel.1.9 = 14989
D [18/Sep/2010:21:36:25 +0200] [Job 499] prtMarkerSuppliesLevel.1.10 = 14989
D [18/Sep/2010:21:36:25 +0200] [Job 499] ATTR: marker-levels=-1,-1,-1,-1,-1,99,99,99,99,99
D [18/Sep/2010:21:36:25 +0200] [Job 499] Getting supported attributes...
D [18/Sep/2010:21:36:25 +0200] [Job 499] Set job-printer-state-message to "Zieldrucker existiert nicht!", current level=ERROR
D [18/Sep/2010:21:36:25 +0200] [Job 499] Backend returned status 4 (stop printer)
D [18/Sep/2010:21:36:25 +0200] [Job 499] Printer stopped due to backend errors; please consult the error_log file for details.
D [18/Sep/2010:21:36:25 +0200] [Job 499] End of messages
D [18/Sep/2010:21:36:25 +0200] [Job 499] printer-state=5(stopped)
D [18/Sep/2010:21:36:25 +0200] [Job 499] printer-state-message="Zieldrucker existiert nicht!"
D [18/Sep/2010:21:36:25 +0200] [Job 499] printer-state-reasons=paused

Accessing the web server on 192.168.1.104 works fine.

Anything I am missing here? Karmic Koala here.

---

