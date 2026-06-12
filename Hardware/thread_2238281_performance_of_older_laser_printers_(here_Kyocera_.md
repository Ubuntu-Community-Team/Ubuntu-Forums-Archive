---
title: "performance of older laser printers (here: Kyocera FS-1010)"
date: 2014-08-07
forum: Hardware
---

### Post by info-gal on 2014-08-07
Hi all,

I use a Kyocera FS-1010 laser printer, with standard RAM, and a D-LINK print server.
After upgrading my laptop from 10.10 to 14.10 (quite a jump there) I get into trouble when I print documents with more than 2 or 3 pages.
Trouble means: Missing half pages, or printer code (PCL, PS) instead of rendered pages.

To drive the printer, I have been using both the Foomatic/hpijs-pcl5e driver and the Postscript driver with the matching PPD.

Are the new driver versions simply more "demanding"? What can I do to get a good performance again?
I used to use a tool called "pdf14topdf13" to sortof downgrade pdf files earlier. Wonder if this kind of postscript downgrading could be
embedded in the print process.

Thanks guys
felix

---

### Post by tgalati4 on 2014-08-07
Look in /var/log/cups for errors in your log files.  Since this is a laptop, are you using wireless to send the print job?  Sometimes a wireless problem will cause a print job to fail.  Try connecting with an ethernet cable to see if the print jobs work OK.

---

