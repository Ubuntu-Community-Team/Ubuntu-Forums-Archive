---
title: "Canon S100 Printer not working yet"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by mik9dt on 2006-08-18
Hi, I have read threads about getting canon printers working in Dapper Drake but have yet to get my Canon S100 USB printer to work. It installs, prints a test page and looks set to go.
Any actual print job results in the following status report

Ready: /usr/lib/cups/filter/foomatic-rip failed

state: Stopped:job stopped

Aaaaargh.

If by any chance you should know how to solve this issue, please reply with a step by step guide for a complete beginner.

---

### Post by ciscosurfer on 2006-08-18
To save room for a longer post if nec., what steps have you already tried?

---

### Post by mik9dt on 2006-08-18
Hi, well to be honest, not a lot really except to spend hours looking for clues, I have read up existing threads and mostly they apply to other canon printers the pixma range etc.
Any help would be truly appreciated, I have resorted to using an old epson printer for the moment but would like to get the canon S100 working with Ubuntu.....

---

### Post by zxee on 2006-08-18
The printer you posted about is supported [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-S100](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-S100)
Note the driver the above site says it works with.
Then click on the upper menu bar System>Administation>Printing>New Printer
Hope that helps.

---

### Post by mik9dt on 2006-08-18
Hi zxee,
thanks for the info, sadly this makes no difference to the original behaviour.
I see that the note says "mostly" works....
I wonder if my computers spec might help diagnose the problem
It is an Athlon XP 1900+
Asus A7-266 motherboard (VIA KT266A chipset)
1 GB RAM

---

### Post by mik9dt on 2006-09-22
Aha, I finally solved this.
I installed a netgear wgps606 printserver so that the Canon S100 could be used as a networked printer.
I found this link
[http://www.cups.org/articles.php?L317](http://www.cups.org/articles.php?L317)
Now I have a networked Canon S100 and an Epson Stylus photo 790. Both printers work well from the 3 Ubuntu and 3 Windows XP computers on my home network.

---

