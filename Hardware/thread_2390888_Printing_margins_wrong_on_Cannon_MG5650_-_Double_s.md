---
title: "Printing margins wrong on Cannon MG5650 - Double sided only"
date: 2018-05-03
forum: Hardware
---

### Post by multibot on 2018-05-03
Hello 

I have a frustrating problem with printing  duplex or double sided. The odd pages all have no top margin and print right at  the top of the page. In fact they appear to top justify so that the  amount shifted up changes to put the first printable thing at the top.  Turn over each sheet though and the even pages on the other side are  fine. Single sided printing has no problem.

This happens with  everything: Firefox webpages, pdf's in Firefox, pdf's in Evince and  other viewers. However LibreOffice Writer shows slightly different  behaviour - the odd pages still top justify, but not to the very top of the paper,  only to a margin about 22mm from the top.

The behaviour when  using "Pages per side: 2" might throw some light on  the problem. In this case the odd paper sides (with document pages 1,2  and document pages 5,6 etc.) are shifted in the same way, while the even paper sides  (with document pages 3,4, etc.) print OK.  This seems to show that it's really  the odd paper sides that have the problem, not the odd pages of the  document being printed.

The problem does not occur when printing from Windows, so it's not the printer.

Printer:   Cannon MG5650
Ubuntu printer settings make and model reads:  Canon MG5600 series - CUPS+Gutenprint v5.2.11
ppd file:  /etc/cups/ppd/Cannon-MG5600-series.ppd
Ubuntu 16.04

Any ideas how to fix this please?  Any suggested changes to the ppd file ?
What do the duplex settings in my ppd file all mean, or where are they documented, if that might be the cause ?

Thanks

---

