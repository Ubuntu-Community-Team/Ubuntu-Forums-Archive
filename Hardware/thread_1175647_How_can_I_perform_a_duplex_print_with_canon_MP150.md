---
title: "How can I perform a duplex print with canon MP150"
date: 2009-06-01
forum: Hardware
---

### Post by chim on 2009-06-01
I install printer driver using a package from Ubuntu 9.04 ( CUPS + Gutenprint V 5.2.3) and I can print normally.
But when I perform a duplex print, the printer still print only on 1 side 
How can I correct this problem? and is there any software or other driver that can perform a duplex print or not?

---

### Post by cariboo on 2009-06-01
Go into the cups management page and check the printer settings to make sure duplex is enabled. To access the web interface type:

```
http://localhost:631
```

in the url bar of your favourite web browser.

---

### Post by chim on 2009-06-03
I have already enable the 2 sided printing in CUPS printer management
but it still print on only 1 side (I test by printing document that has 2 pages it print 1st page correctly but instead of lets me to turn the paper for print the 2nd page. the printer print the 2nd page in another paper but in the upside down position?) :(

---

### Post by fermulator on 2009-06-20
EXACT same issue here.

Duplex (2 sided printing) is enabled in the default CUPS driver configurations.

Typically (with Windows drivers), if one enables duplex printing, the system will print odd (or even) pages first, then show a nice little diagram on how to manually remove the paper, turn around, and re-insert.  Then the user presses "ok I did it", and the printer prints the even (or odd) pages.

This is otherwise known as "manual duplex".  It doesn't seem to work at all ... are we missing something?

---

