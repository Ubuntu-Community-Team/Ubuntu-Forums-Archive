---
title: "samsung scx-4200+ubuntu 9.04+OOo3.0.1"
date: 2009-04-28
forum: Hardware
---

### Post by fland on 2009-04-28
Here is the problem. While printing A4 pages in OpenOffice Writer it's printing like on letter paper type, but not like on A4. Drivers for printer - from openprinting SpliX 2.0.0-rc2 (OpenPrinting LSB 3.2). While printing test page there is no problems with page size. Also while printing from gedit there is no problem with page size, it prints near to the page border. But while printing from OOo I had to set top border up to 2-3cm. I'm tried to use samsung unified driver - but not result. But in ubuntu 8.10 it worked properly with open printing drivers, and with samsung unified driver there was the same problem.
Also in printer settings I set media size to A4, but when opening printer settings from OOo the Paper size is set to letter, and if I change it to A4 and then close OOo and open it again the paper size is again has the value letter. Also changing paper size from printer properties in OOo takes no results while printing, I can set it to A3 or A5 or C6 and result of printing will be same for each size.
Any advices?

p.s. I tried different ways of setting up printer but no difference. I think that OOo just doesn't understand that I want to print on A4, and any changes takes no effect :(

here is the solve: [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/369503/comments/3](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/369503/comments/3) thank to lhamada

---

### Post by fland on 2009-04-29
some updates.
I found file with ppd from splix driver. It was easy to understand, and I decided to make some changes. Every default value of paper settings I'd changed from letter to A4. Also I'd changed some other settings like toner density and etc. Then in printer driver settings in Administation=>Printing I chose Provied PPD file and there I'd chose my changed file. But Media Size again was set to Letter, but other changes, like toner density, time to poweroff, etc toke the effect. I was very interest. Why paper size didn't changed I cann't understand.
Any ideas?

---

### Post by lhamada on 2009-05-01
Check following launchpad item for a clue. 
 
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/369503](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/369503)

Good luck.

---

### Post by fland on 2009-05-02
> **lhamada said:**
> Check following launchpad item for a clue. 
 
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/369503](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/369503)

Good luck.

Thank you. There was great advice. In that article was great comment: [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/369503/comments/3](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/369503/comments/3)

Problem solved :)

---

