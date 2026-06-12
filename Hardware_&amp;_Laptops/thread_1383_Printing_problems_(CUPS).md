---
title: "Printing problems (CUPS)"
date: 2004-10-20
forum: Hardware &amp; Laptops
---

### Post by gluon on 2004-10-20
I'm having problems wth CUPS. My printer is HP 656C, and I've gotten it to work before when using Gentoo.

The problem is that when I add the printer by using Computer - &gt; System Preferences - &gt; Printing the printer is not automatically detected and the application finds 16 USB ports. Thats 14 too many.

I have resolved this in Gentoo by upgrading/downgrading CUPS but I'm not familiar with Ubuntu. How should I proceed?

---

### Post by Nomad on 2004-10-21
Same problem

---

### Post by adbak on 2004-10-21
Enable the universe repository and download cupsys-driver-gimpprint and cupsys-driver-gimpprint-data.  Make sure that you remove any print configuration that you have, then open Computer &gt; System Config &gt; Printing, double click Add Printer.  Make sure that Local Printer is selected and that at the bottom is says USB printer or Parallel printer, depending on your printer's connection.  My advice is to start with the lowest numbered ones first.  Then click next and find your printer's driver.  Finish adding it and it should work.

---

