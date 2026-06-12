---
title: "Installing a printer via wireless connection"
date: 2009-01-07
forum: Hardware
---

### Post by grnida on 2009-01-07
Fairly new to Ubuntu and Linux.  Trying to install a printer via wireless connection.  Can you help me with setup or tell me where to find instructions to do so for my printer?  We have a Konika Minolta magicolor 5450.  Thanks!

---

### Post by eatberrys on 2009-01-07
When i set up my printer i used CUPS my printer is attached to a apple air port extreme

to configure CUPS navigate to here [http://localhost:631](http://localhost:631)

---

### Post by stchman on 2009-01-07
> **grnida said:**
> Fairly new to Ubuntu and Linux.  Trying to install a printer via wireless connection.  Can you help me with setup or tell me where to find instructions to do so for my printer?  We have a Konika Minolta magicolor 5450.  Thanks!

That printer is not listed in the openprinting database.  There are drivers however on konica minolta website.

[http://printer.konicaminolta.net/support/current_printers/mc5450_sup.htm#Drivers](http://printer.konicaminolta.net/support/current_printers/mc5450_sup.htm#Drivers)

You will need to install the printer driver first.  There is probably a readme file.

Second is this printer hooked up to a router or switch?  I am assuming you are connected wirelessly to this router.

If yes them CUPS will find the printer if it is properly assigned an IP address.

---

