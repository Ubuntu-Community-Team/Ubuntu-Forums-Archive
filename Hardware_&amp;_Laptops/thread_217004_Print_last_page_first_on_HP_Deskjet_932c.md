---
title: "Print last page first on HP Deskjet 932c?"
date: 2006-07-16
forum: Hardware &amp; Laptops
---

### Post by zhenya on 2006-07-16
I recently switched our main desktop in the house to 100% Kubuntu (yay!)

Things are working fairly well, except that we use this as a print server for our HP Deskjet 932c.  My girlfriend has been fairly understanding with the changeover, but she prints a LOT of long reports for school, and since the switch, we can't figure out how to print the last page first.  We print both from the Kubuntu workstation as well as from laptops running Windows XP.  I can't find any kind of option for this either in the Printer settings in Kubuntu nor in the printer settings on the laptops.  Anyone?

---

### Post by ORBiTrus on 2006-07-16
Well, if it ain't in CUPS, and it ain't quickly googled, and it ain't anywhere else...  Why not write one yourself?

No, really.  All printouts are done first as a PS file then converted to whatever language the printer speaks (AFAIK).  So, all you need to do to write a filter that they print to that will reverse the order of the pages before sending it off!  Shouldn't be too hard, if you have the time and a little know-how (read: you know how to write a HelloWorld.c file).  And just think of the ego boost.

Fraid I'm not much help too further - I think I have the know-how, but not the time.

---

### Post by zhenya on 2006-07-17
Thanks for the suggestion.  A little more googling found the answer.  I added ```
*DefaultOutputOrder: "reverse"
``` to /etc/cups/ppd/HPDeskjet.ppd and all seems to be working now.  :D

---

### Post by tonester on 2006-12-17
> **zhenya said:**
> Thanks for the suggestion.  A little more googling found the answer.  I added ```
*DefaultOutputOrder: "reverse"
``` to /etc/cups/ppd/HPDeskjet.ppd and all seems to be working now.  :D

Perfect! This works on my HP PhotoSmart 2575xi as well (had to modify the /etc/cups/ppd/PhotoSmart-2570.ppd file instead). :)

---

