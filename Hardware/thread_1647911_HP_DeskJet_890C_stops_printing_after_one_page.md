---
title: "HP DeskJet 890C stops printing after one page"
date: 2010-12-18
forum: Hardware
---

### Post by keaide2 on 2010-12-18
Have have a HP DeskJet 890C connected to a ThinkPad R60 running Ubuntu 10.04 LTS (Lucid Lynx).

The printer stops printing after the first page. I have aleady added the users to the group "lp" manually to at least have the printer to "release" the first page after printing (I found that hint on some other website), but then it just stops.

The printer has been detected and configured by Ubuntu automatically.

Can anyone help with this? Is there a wrong driver or some other problem?

---

### Post by keaide2 on 2010-12-21
I have tested several drivers:

The "hpijs 3.10.2" driver that is seelcted by Ubuntu by defaut is causing that problem.

Changing to "hpcups 3.10.2" solves that problem, but the printed text is "squeezed". It looks like someone has pressed the characters...

I have then also tried the "CUPS + Gutenberg" driver. That driver also works, but the printout quality is rather poor.

Are there any suggestions what else to do? Is it possible to do anything about the setup of the HPijs or HPcups drivers to solve their respective problems?

---

### Post by keaide2 on 2010-12-26
I (almost) solved the problem. I removed the printer, manually installed the hpcups package and then connected the printer again. Ubuntu found it again and it seems that this time, it configured the printer correctly. All the pages are printed. The only problem that I have now is that the printer only starts printing when I turn the printer on before I boot Linux. Otherwise, I need to disconnect and then re-connect the USB cable to get the printer start working...

... it seems that nothing's perfect... or are there any suggestions?

---

