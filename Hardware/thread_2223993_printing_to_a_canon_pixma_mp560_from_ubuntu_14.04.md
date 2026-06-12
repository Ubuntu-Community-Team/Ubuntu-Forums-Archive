---
title: "printing to a canon pixma mp560 from ubuntu 14.04"
date: 2014-05-14
forum: Hardware
---

### Post by andreapasqua on 2014-05-14
Hi,

I have a canon pixma mp560 printer in my LAN. My desktop runs ubuntu 14.04 (amd64) and it can see the printer.
I know because I can ping it and I can use it a scanner off the box using Simple Scan.

However if I try and set it as a network printer using the printer setting (i.e. by doing Select Device>Find Network Printer and entering the ip address under host), I cannot see the printer.

On a different computer I was able to solve the problem by adding canon official drivers and using the cnij protocol, but I would prefer a different solution for my desktop since it has amd64 architecture and canon doesn't support that architecture. I would prefer not to force that architecture.

Isn't there a better way? After all I can see my printer as a scanner off the box, and also in the list of default drivers my computer has there is one corresponding to my printer, or at least with the right name.

I could appreciate some help.
many thanks

---

### Post by pdc on 2014-05-14
anything here of help?

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)          Publish shared printers connected to this server??

gutenprint [http://gimp-print.sourceforge.net/p_Supported_Printers.php](http://gimp-print.sourceforge.net/p_Supported_Printers.php) feel they support the MP560 so a gutenprint driver should work

---

