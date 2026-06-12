---
title: "Printer (Brother 1240) not working at all"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by altse on 2005-04-22
Hi,

I installed Ubuntu few days ago and everything went nice and smooth.
Until I started trying to set up my printer yesterday. 

Ubuntu recongniced it nicely and recommended driver 1250 to be used, which I did.

But when I tried to print the test page, my printer spit out 20 pages (More was coming, but I took power away from the printer) with cryptic letters on top of first page and just few characters on rest of the pages. 

Is there a way to make this printer to work with CUPS?

I've had it working with lprng on my last debian box and that was after quite a lot of fighting and editing printcap files.


Thanks,
Altse

---

### Post by altse on 2005-04-22
Forget this. I Found what was wrong. I had to change my BIOS setting for paraller port. I changed it to SPP and now cups works nice and clearly.

Altse

---

