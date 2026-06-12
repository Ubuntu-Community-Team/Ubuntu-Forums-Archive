---
title: "How do I connect a parallel printer to ubuntu?"
date: 2015-05-12
forum: Hardware
---

### Post by schmitta on 2015-05-12
In google I entered the following string. How do I connect a parallel printer to ubuntu? I got this ubuntu page that told me to enter the string sudo hp-setup . When I did it brought up a window with ethernet USB and wireless but with parallel port grayed out. When I use the printer (ADD) section it brings up serial, uri and network printer. NO PARALLEL PORT  listed info. How do I use the printer utility to describe the parallel port printer to Ubuntu? The printer is HP DESKJET 500. I have a centronics to parallel port connection on my computer running Ubuntu. I used LPD/LPR part of the network printers and have the proper driver selected from the printer utility but the printer utility says printer not connected.

---

### Post by cariboo on 2015-05-13
Could it be that the parallel port is turned off in the bios?

---

### Post by aikishugyo on 2015-05-13
First check that the parallel port modules in the kernel are working (if they are loaded but still not detecting anything then as the previous poster noted, check BIOS).
I don't know what you mean with Centronics, but I presume still parallel protocol/port on the PC side, not SCSI for instance.
You could also use a parallel-to-USB converter cable (that does bi-directional properly), that would make life a lot easier on the PC side.

---

