---
title: "GIMP problem"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by Silvio Moioli on 2005-04-28
I cannot print anything in GIMP. I have a Samsung-ML4500 correctly configured (and working with other apps), and obviously selected from GIMP's print dialog. Anyone has Ideas? I'm using Hoary with the standard kernel.

---

### Post by packetcat on 2005-04-28
Do you see where it says printer name on the print dialog, that will probably say what you setup but under that where it says printer **model** that also must be your printer.

 Mine originally said postscript 2 or something like that, use the setup printer button underneath to select yours, it's kind of a funky select, you have to scroll through a lot of them in a small window and don't forget to save settings at the bottom.

---

### Post by Silvio Moioli on 2005-04-28
Solved. Got to remove the "-oraw" option from the command line.
The Postscript level 2 driver was appropriate.

Tx anyway.

---

