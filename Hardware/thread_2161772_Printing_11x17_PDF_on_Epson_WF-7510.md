---
title: "Printing 11x17 PDF on Epson WF-7510"
date: 2013-07-11
forum: Hardware
---

### Post by ricegf on 2013-07-11
I connected an Epson WF-7510 multi-function device to a 64-bit Ubuntu 12.10 PC via USB, and installed the epson-inkjet-printer-escpr_1.2.3-1lsb3.2_amd64.deb, iscan-data_1.23.0-1_all.deb, and iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb drivers from [http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=183584&BV_UseBVCookie=yes&infoType=Downloads&platform=OSF_O_LINUX](http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?oid=183584&BV_UseBVCookie=yes&infoType=Downloads&platform=OSF_O_LINUX).

Scanning works great at all sizes I tried up to 11x17.  Printing works great at standard 8.5x11, but I'm unable to print 11x17 pages.

With an 11x17 landscape document loaded into Evince, I selected File > Print..., selected the Page Setup tab, and the Paper Size dropdown lists US Letter and various ISO sizes. I used Manage Custom Sizes to create an 11x17 Ledger size, but printing consistently scales the document to 8.5x11 on the 11x17 paper.

I tried LibreOffice with similar forced scaling.

I rebooted temporarily into Windows 7, and the Epson driver installed there from the CD does list 11x17 and the PDF printed correctly, so this is probably not a hardware problem. 

Has anyone succeeded in printing 11x17 pages on an Epson WF-7010 or WF-7510 printer under Ubuntu?  Any suggestions greatly appreciated.

---

