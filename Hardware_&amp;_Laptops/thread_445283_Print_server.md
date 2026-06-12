---
title: "Print server?"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by quadomatic on 2007-05-15
I have some generic CompUSA print server that I use to plug my printer into my wireless network (plugs into ethernet port of wireless router). Can someone tel me how I would go about setting up the printer thats plugged into the print server so I can print in Xubuntu? All I have are the windows drivers they gave me for it, and I know those are needed to get it working in Windows...

---

### Post by trak87 on 2007-05-15
Is the generic CompUSA print server a computer or a dedicated device?

I've set up a print server on a Linux box and I would imagine it is the same for a dedicated device. You have to define a network printer (System, Admin, Printing, New Printer, Network Printer), and then decide the method of sending data to that printer: via CUPS, Samba, JetDirect, etc. The address you put into the "URI" text box is the address of your print server. For example, if you are using a CUPS print server on a computer printing to an HP inkjet, it would be something like: [http://192.168.1.5:631/printers/hp5550](http://192.168.1.5:631/printers/hp5550). How do you determine the address for CUPS? Just surf to the address of your server with a port number of 631 (192.168.1.5:631) and look for the url links in the printer section. Just copy that link to the printer driver.

If you print direct to a network capable laser printer specity JetDirect and the address of the printer, for example: 192.168.1.3

Networked printing is the cat's meow and having experienced it I would never go back to parallel or USB plugs ever again.

---

