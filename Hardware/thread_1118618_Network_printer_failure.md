---
title: "Network printer failure"
date: 2009-04-07
forum: Hardware
---

### Post by oldcelt on 2009-04-07
Network printer is HP Deskjet 840C connected to a Netgear WGPS606 network print server.  All windows machines print to this with no problems.  

This is how I've tried to set up Ubuntu for printing to that printer:
Use printer wizard.
Select network lpd printer
Host (as taken from router list of connected devices) 192.168.0.105
Set lp as print queue
Load correct driver as found in the list
Set text fields to suit.

Try print test page:
Reports connected to 192.168.0.105
Long delay then error:-

Printer State: idle - /usr/lib/cups/backend/lpd failed.

Is the Netgear a "cups" print server by any chance?

Ken

---

### Post by confusedstingray on 2009-04-07
on the netgear does it have  port # for the printers eg 192.168.0.105:9101 
if so try in ubuntu under new printer AppSocket/hpjetdirect and use your ip and port number

---

### Post by oldcelt on 2009-04-07
> **confusedstingray said:**
> on the netgear does it have  port # for the printers eg 192.168.0.105:9101 
if so try in ubuntu under new printer AppSocket/hpjetdirect and use your ip and port number

There are two ports on the Netgear labelled lpt1 and lpt2. Both are USB ports.  The printer is attached to lpt1 - should I use 192.168.0.105:lpt1?

---

### Post by oldcelt on 2009-04-07
Sorted!  This has been the most difficult problem to solve since moving to Ubuntu from Windoze.

Ken

---

### Post by confusedstingray on 2009-04-17
sorry for the long delay trying to do a rebuild of 2 servers and i work nights

from prior print servers i would treat lpt1 as port 9101 and port 2 as 9102 
so i would use 192.168.0.105:9101 as lpt1 and 192.168.0.105:9102 as lpt 2
can yo log in to the netgear from a web browser eg 192.168.0.105 or what ever ip you gave the print server

---

### Post by oldcelt on 2009-04-20
Hey, no problem.  As I said earlier I managed to sort it.  Thanks a million for your interest and advice anyway.

Ken

---

