---
title: "Double Sided Printing (w/o Duplex)"
date: 2005-09-29
forum: Hardware &amp; Laptops
---

### Post by Phalanx747 on 2005-09-29
Hey all,

I bought a Samsung ML-1610 laserprinter for a mere 80 euro's the other day and hooked it up to my pc. CUPS didn't have a driver for this printer and, for the life of me, I couldn't figure out how to properly set-up the Samsung drivers. I found somewhere on the web that I should use the CUPS ML-1510 drivers and indeed, that worked perfectly.

So, on to my question. The printer doesn't have a duplex module but I was wondering if there was any way to enable some sort of software-based manual double-sided printing. In other words, it would print the odd pages first and then allow you to re-feed the printed pages to enable the even pages to be printed on the back.

I know that on Windows printing-dialogs contain a odd/even pages option, but I have yet to find it on ubuntu. And to make matters worse, many applications use different printing dialogs, which each have different options to choose from.

I would really appreciate any help you could offer me with this issue.

---

### Post by Phalanx747 on 2005-09-30
Anyone?

---

### Post by chunk on 2006-01-24
Yeah I have the same problem.

Does anyone know how to print just eve/odd pages?

---

### Post by ekarni on 2006-01-24
Adobe reader has that option.  In the print dialog, there's a pulldown that defaults to "all pages in range" but can be changed to even/odd.

---

### Post by mvaniersel on 2006-04-05
Unfortunately evince and Open Office don't seem to have that option. Wouldn't it be great if that option was available in all printing dialogs? It would save a lot of trees.

---

### Post by Teleyinex on 2006-04-19
The same here. I dont understand why this is by default in all the gnome-cups-manager dialogs for printing. To solve this I use kpdf, which has the option.

---

### Post by Teleyinex on 2006-04-24
It seems that there is a new version for printing in gtk, the info here: [http://blogs.gnome.org/view/alexl/2006/04/21/0](http://blogs.gnome.org/view/alexl/2006/04/21/0)

---

### Post by mihai.ile on 2007-01-16
well here in dapper and this feature stil does not exist :(
why is so dificult to integrate??
this is a really usefull feature.

---

### Post by metalqga on 2007-02-03
You can simply choose to print odd 1,3,5,7,9,... pages first..  then flip the paper and print the even 2,4,6,8,.. pages.
Happy printing, happy trees! :)

---

