---
title: "[SOLVED] Epson printer prints black pages from applications"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by sstalpers on 2007-10-13
When I print from any application (OpenOffice Writer/Calc, Firefox) I get only solid black pages. Strangely enough, when I print a test page I get a proper result. Do you have an idea what could be the problem?

I am printing on an Epson Stylus Color 400. I am using the "stcolor" driver which is default for Ubuntu. I tried other drivers (e.g. Gutenburg CUPS, recommended by Epson) without result.

I am using Ubuntu Feisty Fawn (7.04). I migrated from WinXP recently and am very pleased with Ubuntu so far.

---

### Post by ajgreeny on 2007-10-13
A silly question perhaps, but are you certain you haven't got the default setup of the printer to just use the black ink cartridge?  Just check in printer properties and change it if need be.

---

### Post by sstalpers on 2007-10-14
Thanks ajgreeny, your 'silly question' was spot on!

I had set Dithering to 'Monochrome, fast' since by default I don't print color.  I changed Dithering back to 'Colour, fast, CMYK' and printing works fine now!

Many thanks :)

---

