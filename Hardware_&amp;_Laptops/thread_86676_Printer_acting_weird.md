---
title: "Printer acting weird"
date: 2005-11-06
forum: Hardware &amp; Laptops
---

### Post by chimera on 2005-11-06
I have an EPSON Stylus C24UX printer,which CUPS detected as a local printer(which it is).When I sent it a test page,it started printing it normally,but the output was far from what I expected.Some parts of the page weren't even printed and some were blacked out. Now,I've tried this printer ona windows PC. After messing with the drivers I got it to work,and it printed normally,nothing seemed wrong on the page I printed. Just for the sake of it,I booted in ubuntu and tried it again,with the same results as before.I tried it on all DPI resolutions,and nothing changed at all.

HELP

---

### Post by Teroedni on 2005-11-06
Your sure you not mean Epson Stylus C42UX
[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)
it needs  Needs cupsys-driver-gimpprint from universe.

TRy to install the cupsys-driver true synaptic and see if that soles your problem:=)

---

### Post by chimera on 2005-11-06
Linus bless you,it works OK now!

---

