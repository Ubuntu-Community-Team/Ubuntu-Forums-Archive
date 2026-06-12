---
title: "How to add Brother MFC-J5720DW all-in-one printer"
date: 2016-05-27
forum: Hardware
---

### Post by uli9 on 2016-05-27
Ubuntu 16.04 64bit
I am trying to add a Brother MFC-J5720DW network printer. I downloaded the printer driver deb package from brother website and opened it with software installer. It installed. I followed the directions on the website (not the install part).
When I use printer GUI to add printer there is 2 options:
LPD/LPR queue 'BINARY_P1'
or
IPP network printer via DNS-SD
I tried both. It searches for a driver and then the list to choose a driver comes up. But this printer is not listed.
How can I add it? Why doesn't it find the installed driver?

Or do I need the CUPS driver?

---

### Post by him610 on 2016-05-27
Hello uli9,
You need to go back to the Brother download page...
[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj5720dw_us_eu_as&os=128]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj5720dw_us_eu_as&os=128")
Download the *Driver Install Tool* and run it.

If you need any more help, I have documented how to install drivers for Brother MFC here...[http://ubuntuforums.org/showthread.php?t=2322192]("http://ubuntuforums.org/showthread.php?t=2322192")

Follow the instructions.

---

### Post by uli9 on 2016-05-31
@him610
Thank you! That worked perfectly.

---

