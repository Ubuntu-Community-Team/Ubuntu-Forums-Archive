---
title: "problem with epson epl-5800 printer"
date: 2006-09-12
forum: Hardware &amp; Laptops
---

### Post by LegolasV on 2006-09-12
HI guys, I'm having problem with this printer. My roomate have a machine running Windows Server 2003 and share a Epson EPL5800 printer. I was trying to add this printer to my Ubuntu Dapper using SMB. Everytime I try to print a test page, it shows: 
Stopped: job stopped
I open Properties menu, there it says:
Ready: /usr/lib/cups/filter/foomatic-rip failed
I did some search over Google and try to follow their intructions in [http://cutecomputer.wordpress.com/2006/01/12/smb-windows-printer-access-from-ubuntu-510/](http://cutecomputer.wordpress.com/2006/01/12/smb-windows-printer-access-from-ubuntu-510/) but still failed.
Here is the content of my /etc/cups/printers.conf :

# Printer configuration file for CUPS v1.2.2
# Written by cupsd on 2006-09-12 19:36
<Printer EPL-5800L>
Info
Location
DeviceURI smb://HUMEPARKGROUP/midgoo:midgoo@HUMEPARK/EPSONEPL.2
State Idle
StateTime 1158060998
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>

Our workgroup is HUMEPARKGROUP, username to access the computer is midgoo, pass is midgoo, the machine name is HUMEPARK
Please help me on this problem. Thanks in advance!

---

### Post by lordgibbness on 2006-11-07
I just want to say a big well done with the latest version of ubuntu - plugged in my epson 5800L and it worked!

I had been trying for ages to get printing to work (always had to rely on my windows system for that!). Now, I've just got a few hardware devices to test in ubuntu and there should be no reason that I can't put linux on my main pc (and demote xp the the spare!).

Rob.

---

### Post by Sef on 2006-11-08
Since you're using Dapper, I recommend reading [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-5800") and see what it says.

---

