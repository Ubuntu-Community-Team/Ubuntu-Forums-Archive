---
title: "Canon LBP 5050n network printing"
date: 2011-06-08
forum: Hardware
---

### Post by pedrofuture on 2011-06-08
I have set up this printer successfully on a PC (AMD 64bit) running Ubuntu 11.04 via network. I downloaded linux driver from canon page where i found .ppd file for 5050n and added new printer thought [http://localhost:631](http://localhost:631).

Added printer looks installed good, but if i try print test page, it say:  Idle - print file sent, waiting for printer to finish...

In the cups panel at [http://localhost:631](http://localhost:631) It reports
"Unable to write print data: broken pipe"


Printer has ip: 192.168.1.86 and printing panel it appears as
socket://192.168.1.69:9100

Any help, why i cant print?

PS : I can ping printer.
PS2: Printing from Win is OK.

---

### Post by ghelbig on 2011-06-29
This appears to be a common bug in Ubuntu 9 and 10.  It worked fine in 8, but has since been broken.

To date I know of no workaround other that to use Windows in a Virtual Box to print.

---

### Post by walt.smith1960 on 2011-06-29
Probably a simple fix.  Change the socket I.P. to match the printer I.P. like this:
socket://192.168.1.86:9100.  The thing I'm concerned with using socket:// is that AFAIK the printer I.P. must not change.  In my case I'm able to assign a static I.P. address to the printer but it's something to consider.

---

### Post by lsluijter on 2011-07-24
Canon CAPT network printers must NOT be defined as network printers to CUPS!!

Follow the documentation as provided by canon with the drivers:

- Install the two drivers
- Define the network printer to cups with the LPADMIN command:
/usr/sbin/lpadmin -p [printer name] -m [PPD file name] -v ccp://localhost:59687
-Define the network printer to CCPD deamon with the CCPDADMIN command:
/usr/sbin/ccpdadmin -p [Printer Name] -o net:[IP address]
-Start the CCPD deamon:
 /etc/init.d/ccpd start


VOILA!!!! LBP5050n printer works with UBUNTU!!!!

---

