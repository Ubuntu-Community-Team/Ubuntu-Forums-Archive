---
title: "Unable to print to Xerox Phaser 6350 DP"
date: 2008-10-16
forum: Hardware
---

### Post by drdan14 on 2008-10-16
I'm attempting to print to a networked Xerox Phaser 6350 DP. Anything I attempt to print shows up as eternally "processing" on the print queue, and a single page prints with the following information (where I've faked the URL of the printer):

POST / HTTP/1.1
Content-Length: 295
Content-Type: application/ipp
Host: [printer].stanford.edu
User-Agent: CUPS/1.3.7
Expect: 100-continue

and then a line of random characters.

Other members of my research group can print to this printer, including people using Ubuntu PCs and Windows PCs.

I've tried changing the driver to generic postscript, as well as using the Xerox driver from their web site at [http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=6300_6350&Xlang=en_US&Xcntry=USA](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=6300_6350&Xlang=en_US&Xcntry=USA), both with the same effect.

Does anybody have any ideas as to what I'm doing wrong?

I'm using Ubuntu Hardy Heron with the following result from uname -a: "Linux dualcoredan 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux."

Thanks!
Dan

---

### Post by phidia on 2008-10-16
I could be wrong but when setting up that networked printer you need to choose AppSocket/HP JetDirect and in the Hostname box you need to enter the actual url location of the printer. 

If you've already done that maybe you need to delete the current printer and start over?

---

### Post by drdan14 on 2008-10-20
Thanks, phidia, but I've already taken those steps. It's set up as a jetdirect printer with the proper URL (evidence is the fact that it prints that page of nonsense), and I've already deleted the printer and tried from scratch to no effect.

Is there anything else I can check?

Thanks!
Dan

---

