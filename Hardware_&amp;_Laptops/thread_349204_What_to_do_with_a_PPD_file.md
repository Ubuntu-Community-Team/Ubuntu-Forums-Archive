---
title: "What to do with a PPD file?"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by jdpipe on 2007-01-29
Hi all

I'm trying to get an office network printer set up on my Ubuntu 6.10 machine. The printer is not listed in the CUPS database ('Add Printer') but I found a PPD file listed on Linuxprinting.org

Problem is: I don't know what to *do* with that file in order that I can print.

Also, I installed the deb package with linuxprinting.org PPDs but they didn't appear to show up in the CUPS database. Is there something extra required?

Cheers
JP

---

### Post by tweedledee on 2007-01-31
To use your ppd, add a new printer, and when you come to select the printer, point it to the file instead of selecting from the available installed ones.  It will then install the ppd file - sometimes I then have to go through the install again (but this time selecting from the list to choose the installed ppd), because it doesn't always take when you use a new ppd.

---

