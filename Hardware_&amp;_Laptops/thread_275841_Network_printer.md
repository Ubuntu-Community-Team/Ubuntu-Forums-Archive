---
title: "Network printer"
date: 2006-10-11
forum: Hardware &amp; Laptops
---

### Post by Mcqueen on 2006-10-11
Hi all I need help setting up my mfc-420cn network capable printer. I used the tutorial and have the right drivers but when it ask me for the ipp i put in the ip address, is this correct? I could use all the help even a starting over from the begining. Thanks everyone

---

### Post by rainbowbuilder on 2006-11-06
On Edgy I use the following file as the printers.conf Note I use socket instead of ipp. This is for a network printer on IP address 192.168.1.102 (change as appropriate)

> 
# Printer configuration file for CUPS v1.2.0
# Written by cupsd on 2006-06-16 10:30
<DefaultPrinter MFC420CN>
Info MFC420CN
DeviceURI socket://192.168.1.102:9100
State Idle
StateTime 1150478613
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>


---

### Post by tajreed on 2006-11-06
[http://hplip.sourceforge.net/install/step4/setup/net.html](http://hplip.sourceforge.net/install/step4/setup/net.html)

---

