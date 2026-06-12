---
title: "Zebra LP 2844 printing 1 copy at a time"
date: 2010-12-21
forum: Hardware
---

### Post by rem1473 on 2010-12-21
I have a Zebra LP 2844 Thermal Label printer.  Ubuntu 10.10 auto detected the printer and gave me a choice of four possible printer drivers to install.  I searched around this forum and found that EPL2 was the correct choice.  I installed EPL2 and the printer works well, with a few quirks.

My main problem is quantity of copies.  It does not matter how many I enter in the field, I always get one copy.  I need to be able to print many copies (sometimes 100+) and hitting print that many times does not seem like a good option!

The second problem is not as big a deal.  Every time I print from gLabels, the printer defaults to 300dpi.  When I print at 300pdi, it prints the image much too large.  Changing to 203dpi causes the printer to print at the correct size.  I changed the "default" setting in System->Administration->Printing to 203dpi, but glabels always jumps to 300dpi.  OpenOffice uses the correct 203dpi setting.  

I used cups-pdf to print a PDF of my label from glabel and then open the PDF in Document Viewer, to try printing from there.  The printer will only output one copy at a time, but for some reason it does default to 203dpi.

I can live with remembering to set the DPI everytime, but I really need to be able to print multiple copies.  Please help!

---

### Post by rem1473 on 2010-12-21
Hey, I solved my problem myself!  It feels empowering when that happens.  I opened up the ppd file and made an edit to allow multiple copies.  The ppd file was located at:

/etc/cups/ppd/Zebra--LP2844-.ppd

In the ppd file, I found the following line:

*cupsManualCopies: False

I changed it to true:

*cupsManualCopies: True

I tried restarting cups, but somehow took down printing from the entire system.  I rebooted and it is working fine now!  I found some lines that might be able to limit the dpi to 203, but I don't have time to mess with it right now.  Too busy printing a couple hundred labels! :-)

---

