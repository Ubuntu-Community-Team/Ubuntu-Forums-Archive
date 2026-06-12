---
title: "Panasonic DP-C262 Printer"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by mstrlocke on 2007-02-16
I'm using Edubuntu 6.10 on an HP Pavillion ze5270.

The printer at my office is a Panasonic DP-C262.  It's actually a large photocopy machine, but you can use our wireless network to print directly to it.  

To do this requires installation of a driver, which comes on a CD Rom and is, as far as I can tell, windows compatible only (.dll format).  

I've been to Panasonic's website, linuxprinting.org, and everywhere Google has taken me with a search of "Panasonic DP-C262" and "Linux" but there doesn't seem to be a linux compatible driver out there.

Am I totally out of luck on this one, or is there another way?

---

### Post by deepfriedsushi on 2007-06-10
We have the same printer at my office.  I got it to work by using the hpijs driver for the HP Colorjet 4500.  It at least lets me print in color.  Good luck to ya.

---

### Post by bill-linux on 2007-07-30
Good to 

[http://panasonic.co.jp/pcc/products/en/mfp/download/dp-c322/ps/eng.html](http://panasonic.co.jp/pcc/products/en/mfp/download/dp-c322/ps/eng.html)

On a WINDOWS machine download and run psc3ae051208.exe. This will put the ppd files for your print on your hard drive -- then copy them over to Ubuntu and load up with CUPS. 

A note: These seems to be the right PPD in that it gives all the right options for the machine - duplex, color, etc - but I am having some trouble printing on the next work to our Panasonic copier. When I print to a PS file and examine it, it appears fine -- using, say, ghostscript (gs). When I sent it over the next work to the print it prints the first line of the postscript TEXT file and then a 100 blank pages. I don't think this is the PPDs fault .. any help?

---

