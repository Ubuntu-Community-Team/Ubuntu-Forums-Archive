---
title: "HP OfficeJet USB Support in Ubuntu?"
date: 2005-07-17
forum: Hardware &amp; Laptops
---

### Post by dreadthenight on 2005-07-17
I have tried to print a test page to my HP OfficeJet K80 now using two different distributions (Ubuntu 5.04 and the latest Xandros) and two different laptops, and nothing happens.  I see the print job show up and go away as if everything is all set, but nothing prints and the display on the printer doesn't do anything.

I've connected these laptops to a HP LaserJet and printing works fine.

Is there some kind of problem with HP OfficeJet's on Ubuntu (or Linux in general?) when connected via USB?  In both Ubuntu and Xandros, I verified the printer panel was setup for "OfficeJet K80."

I have tried installing Windows 98 and Windows 2000 on these laptops and printing to the OfficeJet K80 and they work fine.  Since this seems like a relatively common multifunction printer, I'm hoping someone can shed light on this?

Thanks!

---

### Post by David Haas on 2005-07-17
I found this thread for you. It describes how another got the HP Officejet K80 to work on Ubuntu: <http://www.ubuntuforums.org/showthread.php?t=26247&highlight=HP+Officejet+K80>

I also notice that Ubuntu has a PPD file for this printer. It's HP-OfficeJet_K80-hpijs.ppd.gz
and it's at /usr/share/cups/model/foomatic-ppds/HP.

Did you select this driver after your printer was selcted in the Gnome printer manager?

David

---

