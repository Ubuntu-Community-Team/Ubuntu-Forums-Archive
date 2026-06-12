---
title: "ricoh r5c592 MMC not working? aspire 5920, hardy"
date: 2008-08-05
forum: Hardware
---

### Post by Ashrael on 2008-08-05
I was amazed at how well everything works right out of the box when installing Hardy Heron, but a few issues remain:

1) my cardreader does not read memory stick pro, which it does on an identical laptop with winxp... Ricoh chipset R5C592..
2) The lights on the left (wifi etc) don't work, minor problem, but they can work so they should, in the end....
3) CIR is not working, chip unknown so far...

any ideas, except installing windows drivers in ndiswrapper?

TIA.

---

### Post by sergiom99 on 2008-08-05
well, please tell us ome specs of your hardware. Post the outputs of:
lspci
lsusb

As for the MMC reader, theres no support for MSPro yet, someone has to code the linux drivers into the kernel. It works with SD cards though. I dont think you can do it with ndiswrapper. a quick search in the forums might shed some light.

post some other specs and will keep working on the other issues.
good luck.

---

