---
title: "Canon ImageClass MF4350D Printer Support?"
date: 2009-12-27
forum: Hardware
---

### Post by rich1939 on 2009-12-27
I bought a Canon Imageclass MF4350D Printer/Fax/Scanner that has a driver for Windows, but I can't seem to find any drivers for Canon Imageclass printers when I try to install it on Ubuntu 9.10.

I looked for drivers or ppd files on Canon's web site, but didn't have any luck.

The interesting thing is that the printer is recognized on my Windows network (in fact, even the fax printer for that model is recognized)...but no luck in finding a driver.

Any suggestions?

---

### Post by edgeconsults on 2010-07-24
i found this 
[http://www.ubun2.com/question/387/canon_mf4350d_laser_printer_64bit_driver_ubuntu_or_linux](http://www.ubun2.com/question/387/canon_mf4350d_laser_printer_64bit_driver_ubuntu_or_linux)

and the driver here:\

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270807.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270807.html)

but couldn't get my printer to print.  it detected and i installed it but it didn't work.

i'm running 64 bit ed and i guess it doesn't work that well with 64 bit.

i did however get the scanning working via this post

[http://ubuntuforums.org/showthread.php?t=1427330](http://ubuntuforums.org/showthread.php?t=1427330)

---

### Post by pdc on 2010-07-25
I see there are drivers on the Canon Europe site as well

[http://software.canon-europe.com/software/0038852.asp?model=](http://software.canon-europe.com/software/0038852.asp?model=)

and I see this type of printer seems to run off a fairly generic driver

UFRII

did you get any error messages?

the other multifunction printers (eg MP series)

usually have a file pstocanonij;

the canon install puts in it 

> /usr/lib/

([I]the full description is /usr/lib/cups/filter/pstocanonij)
[/I]

whereas it should be in 

> /usr/lib64/

ie it would look like 

> /usr/lib64/cups/filter/pstocanonij

I don't know if this is the file for your printer:

but maybe look in the filter directory in 

> /usr/lib/cups/

and see if there are some canon files there:

you could then copy them to lib64?

---

