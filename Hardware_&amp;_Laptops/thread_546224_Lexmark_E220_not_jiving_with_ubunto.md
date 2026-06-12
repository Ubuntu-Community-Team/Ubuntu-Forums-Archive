---
title: "Lexmark E220 not jiving with ubunto"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by pandelid on 2007-09-08
Cant get my e220 lexmark printer to print properly...

Ive tried 2 things.

- Download .deb driver from lexmark and followed instructions.
This results in having the test print page work.
but when printing from web page or open office i only get text - interestingly the text seems to be postscript commands (%! PS-Adobe-3.0, etc, etc)

I also tired the howto document from lihaassa for lexmark printers in general.
Process seemed to work ok, had one issue with not being root so owner issue when executing an alien command - it seemed to be only a warning.  (oddly I dont remember being prompted for the root account when I installed ubunto, dont know what the password should be for root ?)
That a different prob...

If anybody can shed some words of wisdom - id be appreciated.
Thx

---

### Post by darrenlh on 2007-09-24
I am having the exact same problem, too bad the E220 seems to be so rare.
The only thing I find quite confusing is that in the manual states that the driver does not support printing HTML code, or even PDF - you have to convert it to postscript first. I  have tried even plain text, and everything comes out as post script (9 freaking pages before I can cut the power!). I am going to keep looking into this...

---

### Post by darrenlh on 2007-09-25
I found this on their knowledge base:


Currently, printing to a laser product via a USB port is only supported from a Sun Sparc or Sun Ray workstation.

However, certain releases of Linux provide USB options. Allthough support for USB printing is a responsibility of the operating system, it is possible to print via USB with current revisions of these Linux environments:

    * RedHat 7.2
    * Mandrake 8.2
    * SuSe 7.2

Although USB devices are not guaranteed to work with these releases, USB support has improved and is generally reliable with these versions of Linux.

So I guess perhaps it's time to dig up the parallel cable and give it a try?
Although I have used inkjet printers with usb cables on ubuntu...

---

