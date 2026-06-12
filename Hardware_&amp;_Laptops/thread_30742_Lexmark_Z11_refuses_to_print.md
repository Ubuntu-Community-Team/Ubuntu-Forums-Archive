---
title: "Lexmark Z11 refuses to print"
date: 2005-04-30
forum: Hardware &amp; Laptops
---

### Post by a-nubi-s on 2005-04-30
Hi I'm a newbie and need help with something I found in the Warty thread for my printer. It works perfectly in Mandrake just choosing it in the printer setup without any changes but not in Ubuntu.

I got the ppd and driver mentioned in the quote below. Now What folder do I put the ppd in? What commands do I need to run for the driver? Thanks.

Originally posted by umarmung:
> Just an hour after I posted I found the answer, maybe this will help someone else, so here is my solution...
It turned out that I was missing the ppd file and the binary driver. So I went to linuxprinting.org downloaded the ppd file and dropped it into the right folder. Next I got my driver from sourceforge, compiled and installed it. After that the printer works fine.

BTW: This should really be stated in the 'add printer' dialog. When i found my printer in the list, i thought everything is in place and I can print right away.

---

### Post by David Haas on 2005-04-30
a-nubi-s--You did well, of course to set up the Lexmark, but just for the record, the PPD file for your Lexmark Z11 is available in the Ubuntu distro. It's listed as Lexmark-Z11-lz11.ppd.gz at /usr/share/cups/model/foomatic-ppds. 
Happy printing,
David Haas

---

### Post by a-nubi-s on 2005-05-01
Ok, for anyone else who might have this printer. The ppd and driver work great. The instructions aren't in the readme, they're in the install file. The ppd goes into 
usr/share/cups/model

then ./lz11.install 
will compile and take you through everything. IF CUPS isn't set up yet you have to exit the install process and select the lz11 v2 driver through the "add printer" process. Don't print a test page from here. Run the install program again and it will take you back to print the test page. Print quality is excellent and it's fast, even better than in Windows.

HTH

---

