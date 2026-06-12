---
title: "No parallel port, no working printer"
date: 2005-10-31
forum: Hardware &amp; Laptops
---

### Post by Bloot on 2005-10-31
Hi!, I recently made a clean &#161;nstall of ubuntu breezy, and realized that in the moment of configuring my epson stylus c42-sx on parallel port, this one is missing. I can only choose *hp no_device_found* and *usb printer* from *#1 to #16*. None of them worked. I remember in hoary I was able to choose *epson parallel port* and *canon parallel port*, but now they're gone.

How can I make my printer work just like before with the epson parallel port (wich i repeat is missing on breezy)?. Hope the answer won't be to buy an usb printer. :???: 

Thank you very much for your time.

---

### Post by chrisTGc on 2005-12-20
Useing;
$ sudo modprobe parport_pc
and then System>Administration>printing>add printer
solved similair probs for me.best wishes Chris.

---

### Post by Bloot on 2005-12-20
Thanks Chris!. Actually the solution was as silly as enabling parallel port in the bios... shame on me, as I flashed it to a modded version and didn't notice the parallel port wasn't enabled.

Again thanks, many thanks!.

---

### Post by chrisTGc on 2005-12-26
Glad you up and running with your printer.Ime real happy with Ubuntu Breezy its going real well here.

Best Wishes Chris.

---

