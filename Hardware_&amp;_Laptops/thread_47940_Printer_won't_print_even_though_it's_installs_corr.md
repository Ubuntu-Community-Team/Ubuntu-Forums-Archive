---
title: "Printer won't print even though it's installs correctly"
date: 2005-07-10
forum: Hardware &amp; Laptops
---

### Post by svennglenn on 2005-07-10
I have my Canon BJC 250 with the gimp-print driver installed
and when i try to print something it's shows up in the printer
dialog and says that it's printing. But the printer doesn't seem
to react.

Ubuntu detects and installs the printer correctly so I'm not
sure what the problem is...

---

### Post by David Haas on 2005-07-11
svennglenn--I assume that you selected the Canon BJC250 from the printer list in the Gnome printer manager and then selected the driver (PPD file) for it in the gimp-print/4.2 directory. I see that PPD files for this model are also present in /usr/share/cups/model/foomatic-ppds/Canon. I'd try these--first one, then the other. They are:
Canon-BJC-250-bj200.ppd.gz           
Canon-BJC-250-bjc250gs.ppd.gz        
Canon-BJC-250-bjc600.ppd.gz          
Canon-BJC-250-bjc610a0.upp.ppd.gz

When a PPD file has been selected, Linux places an unzipped copy in /etc/cups/ppd. Was the gimp-print file you selected placed here?

One other crazy thing: Members have stated that their printer only works if it's turned on before booting Ubuntu. So, you may as well try this first. 

David

---

