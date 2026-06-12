---
title: "Printing via a local network"
date: 2008-05-29
forum: Hardware
---

### Post by ludgot on 2008-05-29
I have a home network connected to the web by a router/firewall. I have 3
computers and one print server connected to the router. They have IP addresses in the range 192.168.123.x. One PC runs Windows Vista, one runs Ubuntu 6.06 and one runs Ubuntu 8.04. I would like to use the common printer from all my PC:s with the IP printing protocol (IPP). It works perfectly well withthe Vista machine but with neither of the Ubuntus. The print server is a Level-One FPS-9021 with a Centronics interface physically hooked up to my Centronics printer. The print server can be accessed via its own web interface and it confirms that it supports IPP. I can ping it from all myPC:s. I have tried to configure the printery with CUPS - problem is that CUPS won't let me get as far as to specify the driver (Canon BJC-4400) which exists on 6.06 and 8.04. When I try New Printer->IPP CUPS suggests that I specify a host and a queue for it. If I give the host as localhost or IP address (of localhost or print server) CUPS replies that it is not possible to specify a queue for that host - and that's it. Isn't there a way to do this by updating a few control files in /etc/...? Please help!

---

### Post by ludgot on 2008-07-10
I have succeeded to enter a network printer and it appears as follows
in the CUPS entry for 'IPP-printer':
host: 192.168.123.4
queue: /printers/canon-BJC-4400
url: ipp://192.168.123.4/printers/canon-BJC-4400
When I hit the print-test-page button CUPS returns ...submitted as job # x.
My router lights for localhost and print server flash repeatedly and so
does the network light on the print server itself but nothing comes out
of the printer.
When I check the troubleshooting option for 'ipp-printer' it returns:
'Printer's state message: Connecting to 192.168.123.4 on port 631'
'Printer's state reason: Connecting to device'
If I click forward after this - CUPS will die (greying)
Do I have to make a separate entry for the server and one for the printer
itself or whatever ?

---

