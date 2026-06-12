---
title: "USR9108 print server problem"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by CassioBunana on 2007-01-02
Hi guys, I do hope someone can give an hint....I'm working happly with my Amilo M7400 laptop running Kubuntu but I'm not able to print on my Samsung ML-1610 printer connectied via USB to an USR9108 router.
Some informations:
- printer works fine if connected directl to my laptop on USB;
- router works well;
- CUPS seems to have no problem;

When I try to print the test page nothing happens, the job remains in the queue endlessly with no error messages. I've set up the printer has an IPP whit address [http://192.168.1.1:1631/printers/printer_name](http://192.168.1.1:1631/printers/printer_name) as suggested in every manuals I found.

I've tried also different ppd for my model but no difference!

KPrint also detect the printer scanning the subnet and the problem is the same if I use WiFi or LAN connection...

What should I do?

---

### Post by vmalep on 2007-01-13
It will not help you a lot but I have a similar problem. The strange thing is that it sometimes works. The printer being located in another room, I do not notice immediately what is going on and I have not yet found the reason why it doesn't work (or why it works...).

To be noted that a friend running Windows XP can print without problem (I did not tell him yet that it does not work with Linux...).

I tried with Gnome and KDE (same problem). I tried modifying the printer from the USB port to [http://[ip]:1631/printers/](http://[ip]:1631/printers/)[printer name], etc. To no avail so far...

Distrib: Edgy (Ubuntu + KDE installed afterwards)
Printer: HP Deskjet 5440
Print server: USR9108

Pierre

18/01/07: Ça fonctionne de nouveau. Ce que j'ai fait depuis la dernière tentative, c'est de redémarrer le router... C'est peut-être la solution.

---

### Post by woodstock84 on 2008-04-05
I have the same problem too.

I have two machines one with Kubuntu and XP and the other with Fedora and XP. When I try to print a document, it seems like the print job is queued and directed to the printer without any problem but no result.

I tried several things; first, I tried to add multiple versions of the same printer -of course in XP, I switched the port of the USB printer to TCP/IP port, I changed the name of the printer from the modem setup page, but none of these seem to provide a lasting solution to the problem.

I've observed -and read in other forums- that this is probably caused by the printer itself; my HP LaserJet 1020 has no buttons on it and I don't reckon any way to reset the job queue of the printer. I tried some "scenarios" -like no paper case, or disconnection-, and I observed that the printer, while connected to the computer via USB- send a message to the computer that there is a problem with the printing. I think that is the main problem; either the router's print server or the printer itself is unable to redirect any troubleshooting message to the printing user. I tried this scenarios with my OSs in various setups, still no solution.

I may report this to HP, maybe they will have a nice and easy walkthrough for this problem.

Good day

---

