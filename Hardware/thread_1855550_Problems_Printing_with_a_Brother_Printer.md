---
title: "Problems Printing with a Brother Printer"
date: 2011-10-06
forum: Hardware
---

### Post by vsh3r on 2011-10-06
Hi,

I'm having problems printing with a Brother HL-2140 series printer.  It was working several months back and now it isn't. 

When I try to install the Linux drivers from Brothers website I get this.

ERROR:
Lintian check results for /home/asher/Desktop/brhl2140lpr-2.0.2-1.i386.deb:
E: brhl2140lpr: maintainer-address-missing Brother Industries,Ltd 

SPECS:
[http://www.brother-usa.com/printer/modeldetail.aspx?PRODUCTID=hl2140&tab=spec](http://www.brother-usa.com/printer/modeldetail.aspx?PRODUCTID=hl2140&tab=spec)

DRIVERS: (non linux)
[http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/download_top.html?reg=us&c=us&lang=en&prod=hl2140_all](http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/download_top.html?reg=us&c=us&lang=en&prod=hl2140_all)

DRIVERS: (linux)
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2140](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2140)

LOCATION:
usb://Brother/HL-2140%20series  

GOOD:
It successfullly detects the printer and starts a print job.

BAD:
It prints blank pages.

Any ideas?

:confused:

V$H.er

---

### Post by hilz on 2012-01-31
> **vsh3r said:**
> Hi,

I'm having problems printing with a Brother HL-2140 series printer.  It was working several months back and now it isn't. 

When I try to install the Linux drivers from Brothers website I get this.

ERROR:
Lintian check results for /home/asher/Desktop/brhl2140lpr-2.0.2-1.i386.deb:
E: brhl2140lpr: maintainer-address-missing Brother Industries,Ltd 

SPECS:
[http://www.brother-usa.com/printer/modeldetail.aspx?PRODUCTID=hl2140&tab=spec](http://www.brother-usa.com/printer/modeldetail.aspx?PRODUCTID=hl2140&tab=spec)



DRIVERS: (non linux)
[http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/download_top.html?reg=us&c=us&lang=en&prod=hl2140_all](http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/download_top.html?reg=us&c=us&lang=en&prod=hl2140_all)

DRIVERS: (linux)
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2140](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2140)

LOCATION:
usb://Brother/HL-2140%20series  

GOOD:
It successfullly detects the printer and starts a print job.

BAD:
It prints blank pages.

Any ideas?

:confused:

V$H.er

Hi Vsh.er,

I have a HL-2142 on Ubuntu 11.10, and haven't had blank pages. But I found I could check some details by pressing the <|> button.  It should print a status page even if your computer isn't on. Not sure if you've tried that, just to make sure the printer doesn't have a fault.

Hope this helps to narrow down the problem.

[EDIT] Sorry my mistake it must have been the HL-2040 that did this. I tried my HL-2142 and it won't print by pressing <|>.

---

