---
title: "printing with continuous paper !DESPERATE HELP NEEDED"
date: 2009-10-31
forum: Hardware
---

### Post by ponlerd on 2009-10-31
Desperate help please....
The question is I'm trying hard to print with continuous paper on Epson printer , here are the details
1.Printer = Epson LQ-570 ESC/P2  > no exact driver, i'm using LQ-570+ driver
2.Ubuntu 8
3.The paper size in question is 24.5cm (width) x 8.8 cm(height) continuous paper
4.Settings in printer properties 
 Page size = Custom
 Page region = A4 (no Custom size to select)
5.The document is in Openoffice  Calc 
 Format > Page > paper size to custom already set
Result
The first page is printed properly , no problem at all , the paper size set is ok
but
Between the first page and second page, there is a mysterious SPACE, where actually I don't want a space between the first and second page since it's a continuous paper , the second page should start immediately after the first page ends.

Things that I tried so far:
Change the printer settings at Page region ( the place I said there was no "custom") i changed it to Letter, 3x5, demand draft, lots of stuff, and each setting yielded a different result, the space between the end of the first page and the beginning of the second page changes , but i can't get the setting that will eliminate the space completely.

In windows, the printer settings will have a place where i can change the paper source to continuous paper, but here the paper source setting is greyed out , in the PPD file there is no option to set this paper source either.

I'm trying to do this , if successful, my company can change a lot of computers from windows to ubuntu!!

---

### Post by quixote on 2009-11-01
Weird.  My problem is usually the opposite: sheet paper and printing as if it's continuous in that it'll split an image across two sheets.  I've had no luck solving that problem.  Maybe somebody who knows more about it will jump in.

Only thing I can think to suggest: can you use Gutenprint with that printer?  (It can be installed vis Synaptic.  Search for "gutenprint" and/or "cups-driver-gutenprint".)  If you can, I'm not sure whether it has a continuous feed option, but it solves so many printer issues that it may be worth a try.

---

