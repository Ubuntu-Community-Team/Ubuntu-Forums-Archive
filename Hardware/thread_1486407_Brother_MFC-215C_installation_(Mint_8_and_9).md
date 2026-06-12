---
title: "Brother MFC-215C installation (Mint 8 and 9)"
date: 2010-05-17
forum: Hardware
---

### Post by MrD_scifi on 2010-05-17
I googled around and found the advice on installing the Brother MFC-215C printer confusing and not working for me.  I've just made printing work (yet to try to sort the scanner) by a fairly straightforward method for Mint 8 and 9RC which 'should' work for Ubuntu 9.40 and 10.04. (there may be differences in what you call your menu system)  This may help anyone googling in future as I hope the steps are clear enough:

Download the two packages for the MFC-210C from [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)
You want both the following here on  that page: 

LPR driver 	deb 	1.0.2-1 	740 KB 	2006.Mar.31
cupswrapper  driver 	deb 	1.0.2-3 	12 KB 	2007.Jul.11

The files are called:

mfc210clpr-1.0.2-1.i386.deb
cupswrapperMFC210C-1.0.2-3.i386.deb

**--->**open package Manager and  install "csh"
**--->** plug in  printer and install mfc210clpr-1.0.2-1.i386deb file
**--->**open terminal, enter "sudo  nautilus" browse to "usr/share/cups" directory in the file system,   create a "model" directory, keep nautilus open to watch.
**--->** Install the  cupswrapperMFC210C-1.0.2-3.i386.deb file.  Watch in nautilus as a file  is created in there, brmfc210c_cups.ppd.  this is important!
**--->**Click Menu/Control  Centre/Printing and up comes the printer popup.
**--->**Clicked add new printer.  
**--->**Click on Brother MFC-215C,  click forward and it tries to find drivers.  It fails and offers to add a  .ppd file, choose this option and then click to browse for the .ppd  file that was made in "usr/share/cups/model directory and it will  install your printer driver!!!!  
**--->**You  can now print a test page, which should work, then go on to print your  documents.

---

