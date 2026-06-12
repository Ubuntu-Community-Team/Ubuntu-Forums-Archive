---
title: "Abit VP6 not detecting ANY PCI devices"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by delmar on 2007-03-14
I just thought I would post to share that I came accross an issue with my Abit VP6 Dual CPU board when installing Ubuntu 6.10.   

My issues started when it wouldnt detect any of the network cards I tried. 
Alt-f2 to the spare console, and 'lspci' showed nothing what so ever, not even the Vga, Ide, PCI/ISA Host bridge.. nothing.    Everything worked fine in Windows and all cards detected and worked as expected, so I figured it must be an issue with the PCI and kernel somewhere. 

The cure for me;
I downloaded the latest 'beta' bios from [http://www.vp6-board.com](http://www.vp6-board.com)  (Bios VP6_YTB04). 

The only information I can offer about the previous Bios was the string at the bottum of the screen during Post, which I noted down. 
11/6/2000 694X-686B-6A6LJA1EC-UR  (if I read my hand writing correctly). 

I hope this helps someone out.

Cheers.

---

