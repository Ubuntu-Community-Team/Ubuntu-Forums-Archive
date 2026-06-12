---
title: "Printers in Ubuntu missing from Kubuntu"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by abovett on 2008-04-05
Hi

Anyone know why some of the printers listed in Ubuntu are not present in Kubuntu? That is, adding a printer in Ubuntu using "System -> Administration -> Printing" shows some printers (e.g. most of the the Canon PIXMA series) which are not shown when adding a printer in Kubuntu via "System Settings -> Printers".

I found a workaround in my case - I accessed CUPS via [http://localhost:631](http://localhost:631) and found that the additional printers _were_ listed so I set it up there. Then, when using KDE's printer settings it appears to be listed correctly.

However, it looks like something's wrong - anyone know what?

P.S. I was installing a Canon PIXMA iP4300 and at first attempt the colours were very poor. However, changing the colour model option in the driver from RGB to CYMK seemes to have fixed this. Thought that tip might help someone.

Andy B

---

### Post by entic on 2008-04-24
I'm having this problem, and am not sure what to do with CUPS. Could you do a step-by-step of how you installed the printers from there? It would be much appreciated.

---

