---
title: "Newbie needs help with printer Epson sx105"
date: 2009-12-12
forum: Hardware
---

### Post by capuccino on 2009-12-12
Hi

Im a newbie in Ubuntu and I wonder if someone has managed to install a monitor for this printer

my situation is: I can print, but I can't scan images, see the ink levels, clean the heads or change cartiges

I really need this to forget windows compleatelly, and I wonder if you could help me


Thanks!

---

### Post by IcarusR on 2009-12-12
I believe this is not supported under the current stable version of sane, but is in the development version. 
So you would need to install the development version. 
It is not supported by Image Scan either.

---

### Post by capuccino on 2009-12-14
thanks for the reply IcarusR, Im trying to installing it now thru virtualbox.

it seems possible, lets see

---

### Post by Nightstrike2009 on 2010-02-25
I have a similar thread Regarding an Ink Monitor Utility [http://ubuntuforums.org/showthread.php?t=1415955]("http://ubuntuforums.org/showthread.php?t=1415955") 

I had no replies but I've found a terminal program that does the job called "escputil" check my thread for how to and files needed, I have also found a GUI for it now "Stylus Toolbox" from sourceforge website.

PS: An Epson SX100 is the "little brother" of an SX105, so what works for mine should work on yours, I've solved the Ink monitor problem sorry I couldn't help with the scanner one, though.

---

### Post by luxee on 2010-05-19
Hi there,


I just found it on the forum:

this is for scanning just installed its working
 [http://linux.avasys.jp/drivers/iscan/2.24.0/iscan_2.24.0-4.ltdl7_i386.deb](http://linux.avasys.jp/drivers/iscan/2.24.0/iscan_2.24.0-4.ltdl7_i386.deb)
 this is for printing testing it now
[http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/con...]("http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/contrib/binary-i386/openprinting-gutenprint_5.2.5-1lsb3.2_i386.deb")
 Good luck

---

### Post by ellgor on 2010-05-20
Hi,

If your still having problems with scanning, then try this :

Go to the "Avasys" site and get their Imagescan package, go through the form filling in bit and when you get to the download page scroll right down until you see "Iscan or Imagescan deb" which is a completely seperate app  from the full printing package, once downloaded use gdebi to automatically install it, needs a reboot to work properly.  

REgards, Ellgor.

---

