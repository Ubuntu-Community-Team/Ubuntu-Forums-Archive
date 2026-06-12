---
title: "Canon MF4690 doesn't work in 12.04"
date: 2012-06-17
forum: Hardware
---

### Post by tpistor on 2012-06-17
This all worked in 11.04 and continued to work on 11.10 after upgrade.  On a separate machine with 12.04 I installed the same Canon printer drivers:

cndrvcups-common_2.20-1_amd64.deb 
cndrvcups-ufr2-us_2.20-1_amd64.deb

(I converted rpms to deb with alien)

In installed the printer from the "Printing" GUI - it all seemed fine.

It was missing some print filter, I copied the file:
/usr/lib/cups/filter/pstoufr2cpca from the working (ubuntu 11.10) machine - it was no longer complaining about a filter.

It all seems fine - except that when I go to print a test page, the printer prints the following:

**** Unable to open the initial device, quitting.

No idea how to debug.  Again, this is working on Ubuntu 11.10 laptop, but not in 12.04.

PS - I also tried Canon driver UFRII version 2.4 - same bug.  I don't think it's Canon - I think it's Ubuntu 12.04

---

### Post by tpistor on 2012-06-17
Oh yes...I forgot to mention that this is a network printer

---

### Post by cesare.pellegrini on 2012-06-27
I'have the same problem.

for pstoufr2cpca I make a symbolic link (ln -s /usr/lib64/cups/filter/pstoufr2cpca/usr/lib/cups/filter/pstoufr2cpca)

I'have put in /etc/apparmor.d/local/usr.sbin.cupsd this line:

/usr/lib64/cups/backend/cnusb Uxr,
/usr/lib64/cups/filter/pstoufr2cpca Uxr,
/usr/lib/cups/backend/cnusb Uxr,
/usr/lib/cups/filter/pstoufr2cpca Uxr,

But the printer print always "Unable to open the initial device, quitting"

Cesare

---

