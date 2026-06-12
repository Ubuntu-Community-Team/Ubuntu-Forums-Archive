---
title: "mfc 7420 thinks it is printing"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by rube1947 on 2007-05-27
I have installed all of the drivers for the 7420 and when I print it appears as if I am printing but nothing happens.  Any thoughts?  There is a log of the print jobs saying that they have been completed but the printer does not print anything.  I can run a test page on the printer itself but not from the computer,

---

### Post by The Pinny Parlour on 2008-03-06
Yes I have a similar problem.

Do the following to correct it.

Go here and download the Brother LPR Driver
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/brmfc7420lpr-2.0.1-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/brmfc7420lpr-2.0.1-1.i386.deb&lang=English_lpr)


Then go here and download the Brother Cups Wrapper Driver:
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC7420-2.0.1-2.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC7420-2.0.1-2.i386.deb&lang=English_gpl)

Install the LPR then the Cups Drivers and presto....working.  :)

---

