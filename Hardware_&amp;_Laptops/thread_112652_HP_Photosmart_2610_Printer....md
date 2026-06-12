---
title: "HP Photosmart 2610 Printer..."
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by adssse on 2006-01-04
I am using Ubuntu 5.10 and a HP Photosmart 2610 printer that as used as a network printer. It is connected directly to my wireless router so that all my computers can use it. The setup is working fine on my windows machines but have not yet been able to get it working on my linux machines. I have cups, hplip, hpijs all installed. I also have the HP-photosmart-2600-hpijs.ppd file and have used that so I can selecte the photosmart 2600 line while installing. I am attempting to install by using system->administration->printing. First I selected Global Settings and checked Detect LAN Printers, this did not give me any response so I went on to add a printer. For printer type I selected 'Network Printer' and selected 'Cups Printer IPP'. In a terminal I typed 'hp-makeuri 192.168.1.105' and it gave me this URI: 'hp:/net/Photosmart_2600_series?ip=192.168.1.105', so that it what I put in the URI box. After pressing forward I selecte HP for the make and Photosmart 2600 for the model and clicked apply. At this point it seems to have installed fine but when I go to print a test page it doesnt print. I click on the printer and select properties and next to status there is the error 'Printing: Unable to lookup host 'hp' - Unknown host'. At this point I am not sure what else to try so I would really appreciate any help in accomplishing this.

---

### Post by adssse on 2006-01-07
Any ideas? I have been trying to find more info on what my host should be. The generated URI gave me 'hp' but this does not seem to work.

---

### Post by Amon_Re on 2006-01-07
[QUOTE=adssse]Any ideas? I have been trying to find more info on what my host should be. The generated URI gave me 'hp' but this does not seem to work.[/QUOTE]

Add network printer, protocol: HP JetDirect
host: 192.168.1.105 *(*)*
Port: 9100

Proceed as you did.

This should work.
(*): I'm assuming you're using the proper IP

---

### Post by adssse on 2006-01-07
[QUOTE=Amon_Re]Add network printer, protocol: HP JetDirect
host: 192.168.1.105 *(*)*
Port: 9100

Proceed as you did.

This should work.
(*): I'm assuming you're using the proper IP[/QUOTE]

Thank you very much. I have been trying to get this to work for days. I sincerely appreciate your help.

---

