---
title: "Lexmark X1170 on 16.04 64bit?"
date: 2017-09-05
forum: Hardware
---

### Post by Jan_Johansson on 2017-09-05
Hi, in 14.04 32bit i just had to download a driver(CJLZ600LE-CUPS-1.0-1) and install from teminal, then go to settings printers and add it there, but in 16.04 64bit its different as the driver will not install at all. Looking at the VERY old ubuntu help page its old and probably not valid anymore:


[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

So i need help installing this printer

Can someone help me with this?

JBJ

---

### Post by efflandt on 2017-09-05
Lexmark laser printers are no brainers to get working, because they do postscript (and HP PCL). When I got a Lexmark C543dn before Ubuntu had a driver for that, it worked with a C534 driver. I also have a Lexmark X204n all-in-one that worked with HP printer drivers when I temporarily used it to substitute for a failed HP network printer at work. Its Linux network scanner (sane) driver works in 64-bit 14.04, and virtualbox with 32-bit sane driver in 32-bit 16.04 (that I used for 32-bit only webex), but 64-bit driver does not work in 64-bit 16.04 or 16.10 (maybe due to change in startup scripts in 16.04).

But the only Lexmark inkjet printer I have from long ago was just raster graphics with no built-in fonts (typically considered "Windows only") and the driver had to do everything. Not sure if I ever got it to work in Linux, but I rarely print and any inkjet would tend to dry up.

When I looked up your printer and selected Linux/Unix on Lexmark website, it says "**No drivers or software for this OS were found in the selected language."**

---

### Post by Jan_Johansson on 2017-09-12
Took me a while to find it again in all my help files, but here is the instructions on how to install this printer, in 32bit Ubuntu:

[https://www.dropbox.com/s/5p2ol2mvisjhqbq/Lexmark%20X1100%20printer%20installation%20for%20Peach%20OSI.odt?dl=0](https://www.dropbox.com/s/5p2ol2mvisjhqbq/Lexmark%20X1100%20printer%20installation%20for%20Peach%20OSI.odt?dl=0)

The above works fully in 32bit, problem is that I need a working method for 64bit.

---

