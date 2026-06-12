---
title: "using USB printer"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by weijie90 on 2005-04-28
hi,
im using the hoary release. ny printer is the canon 1320.
when i turn on my printer and run dmesg | tail, i get:

```
usb 1-2: new full speed USB device using uhci_hcd and address 5
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04A9 pid 0x107B
``` 

how should i use this printer to print stuff? thanks!

---

### Post by accuser on 2005-04-28
The easiest way is using CUPS. From the GNOME desktop menu, select System->Administration->Printing. The Printers window appears. Double-click the New Printer icon, and follow the prompts for adding a local printer. When specifying the port the printer is connected to, select USB Printer #1.

---

### Post by Gianni Exile on 2005-04-28
Add a system printer from the control panel, and away you go...

---

### Post by weijie90 on 2005-04-28
but there is this enormous turboprint logo and its really slow. how do i use the printer without turboprint?

---

### Post by weijie90 on 2005-05-04
can anyone please help? thanks!

---

### Post by David Haas on 2005-05-04
I assume that you have cupsys and foomatic packages installed--check this in Synaptic if you haven't done so. After selecting your printer in the printer GUI, what PPD file did you select? I don't see a PPD file for the Canon 1320 listed in either gimp-print (/usr/share/cups/model/gimp-print/4.2) or foomatic (/usr/share/cups/model/foomatic-ppds/Canon).
David

---

### Post by weijie90 on 2005-05-06
sorry, the printer is i320. the only real "driver" ive found for it is turboprint. it is not free and the free version prints big and stupid logos on my stuff. how do i use the canon i320 without turboprint? thx

---

### Post by weijie90 on 2005-05-10
pls help.

---

### Post by dhega on 2005-05-11
I had the same problem with my Canon i560, i HAD to use a different driver to get it to work,

But turboprint was the only good solution.. :(

i have learnt something from this. Never buy canon stuff again..

---

### Post by David Haas on 2005-05-14
Well, I don't see that Hoary contains a PPD file for the Canon i320 either. I also don't see free files for this printer listed at [http://www.linuxprinting.org/](http://www.linuxprinting.org/). So, if free drivers aren't availble for a printer, you could purchase one, as noted by prior replies, or purchase a printer that is supported by Ubuntu or that has available free drivers. HP produces drivers for Linux and gives them to the Linux community for free. Epson also supports Linux. This is discussed, as you may know, at the above Web site. Fortunately, printers have become quite inexpensive: entry level ones can be as low as $40 in the U.S..
David

---

### Post by weijie90 on 2005-05-20
thanks everyone!

---

