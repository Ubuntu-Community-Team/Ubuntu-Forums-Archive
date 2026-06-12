---
title: "Apollo 1200:&quot;I can't believe it's not color!&quot;"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by LordLandon on 2005-12-01
Printers are hardware...right?
Alright, so I have this one little problem that's giving me a headache...I have an apollo 1200 printer that I purchased at least five years ago and recently got a black cartrige for it(cost me more than the printer >.<). The printer works fine on windows, once I change the default color cartrige setting to black. However my ubuntu computer seems to have issues with it. It definetelly recognizes the printer and can comunicate with it, because it seems to at least TRY to print the test page, but winds giving me a cartrige error(same way as it did when windows assumed it was color). So I try messing with the settings, namely color mode. That brought no progress, and man's new best friend - Google shed no light on it either, so now I'm asking here.
So...how would I go about solving this? I'll gladly post more info if needed, so just ask  =)

---

### Post by az on 2005-12-01
So, there is no color cartridge in it or there is, but it is empty?


What settings did you try in terms of color mode?

---

### Post by LordLandon on 2005-12-01
There's a black cartrige in there, and I tried changing color mode to greyscale..as well as the other 3 CMY options, just to be sure. Also, I changed CMY levels to no CMY when the color mode didn't include CMY. Nothing worked.

---

### Post by az on 2005-12-01
I looked here:

[http://linuxprinting.org/show_printer.cgi?recnum=Apollo-P-1200](http://linuxprinting.org/show_printer.cgi?recnum=Apollo-P-1200)

Can you try using the deskjet 400 driver?  If that does not work, I do not remember if gimpprint is installed by default.  You can run this printer using gimpprint as well as the HP stuff.  Maybe give that a try (gimpprint provides the pcl3 driver.)

ijsgimpprint
cupsys-driver-gimpprint

If that works, please file a bug report.

bugzilla.ubuntu.com.  Depending on the solution, the package you need to report the bug to will vary.

---

### Post by LordLandon on 2005-12-01
EXCELENT! Just got it to print the test page =D
Thanks a lot azz ;) 
Solved by selecting the PL 3 driver under the "Generic" category

---

### Post by LordLandon on 2005-12-07
Hmm, seems I spoke too early...Neither Open Office or Firefox are able to print to it o.O

---

