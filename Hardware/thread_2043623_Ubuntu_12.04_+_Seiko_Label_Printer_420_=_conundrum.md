---
title: "Ubuntu 12.04 + Seiko Label Printer 420 = conundrum"
date: 2012-08-17
forum: Hardware
---

### Post by nickTaylor1181 on 2012-08-17
Hiya, possibly a long-shot here:

I'm trying to get a Seiko Smart Label Printer 420 to work with Ubuntu 12.04. 

It works with Windows... so printer/cable are good... in Ubuntu I go to 

[http://localhost:631/admin](http://localhost:631/admin)

and attempt to use any of the ppd files that were provided as drivers on the seiko site... (none say 420... but if I specify 200, it then displays "SII SLP200/420" which may or may not be right).

I also need to edit the siislp200.ppd file from
*cupsFilter: "application/vnd.cups-raster 0 /usr/libexec/cups/filter
to
*cupsFilter: "application/vnd.cups-raster 0 /usr/lib/cups/filter

which may or may not be right.

All looks well enough - but if I try to print anything, I get complete silence... and cups saying

ID 	Name	User	Size	Pages	State
SII_SLP200-49 	Unknown 	Withheld 	1k 	Unknown 	 stopped 

Which leaves me none the wiser alas.


Any idea what I can try next? I'm at a bit of a loose-end on this one, and it just seems wrong in every conceivable way to have to boot into windows just to print labels.




Nick

---

