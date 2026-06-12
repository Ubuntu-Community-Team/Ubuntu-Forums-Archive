---
title: "Printing PDFs"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by tzulberti on 2006-11-16
Hi. I have a samsung 2010, and linux detected it as a 2010, but I have some problems when printing PDFs files...

I have installed kpdf, evince, and acrored. When i print using envince, it doesn't take into account the print Even/Odd pages. When i print from Kpdf, it doesn't take into accout the margins (i have tried to change them from the advanced, but failed). When i print using acroread, it does take into account the print even/odd pages, but not the print reverse option...

I asm using Ubuntu Edgy... Thanks in advance

---

### Post by likwidoxigen on 2006-11-16
Have you tried seeing if there is another driver available for your printer? For example i used to use a postscript driver for my HP1100 then when edgy came about they changed something and I was printing garbage, but after a quick driver change to a generic HP driver all was well. I apologize that i'm not a printer expert but this could very well work. If this does not try using the postscript driver. Hope this helps!

Cheers
Bryce

---

### Post by tzulberti on 2006-11-16
Thanks for answering...
I don't have any other driver... But i change model to 210, and the same thing happens

---

### Post by towsonu2003 on 2007-02-23
did you find a solution to this? or filed a bug report? evince and acroread ignore my margins as well (on Dapper). I had to print the file from MS Windows.

edit: my printer is a hp f340 all-in-one

---

### Post by schumifer on 2007-03-28
Here is something to wonder about.
I have an epson c46 and an epson rx600, both installed and working fine.
I had to print a pdf. I tried with kpdf but the printout came out as if i had chosen landscape but such an option i did not find.
SO searching around i found acroread. Since i have 64bit kubuntu i had to force it a bit but it installed. Tried to print ....   no printers????~~!!!!! 
Anyway it was getting late so i fired up vmware, added a usb xontroller, opened the file with acrobat reader 6 and it rinted like a charm.
Next day i decide i give acroread an other try.
Googling around i found that i had to add the command lp -d "PRINTER" Did just that and the printer started printing. BUT again as if i had asked it to print the page in landscape.
Tried every option i could, only thing that kind of worked was to untick auto rotate and center and tick -hold on now- landscape.....
And here goes the really weird thing. My RX600 works perfectly.
Whatever...

---

