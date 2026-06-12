---
title: "Brother Printer HL-L2380DW, Ubuntu 14.04"
date: 2014-12-09
forum: Hardware
---

### Post by shauna-f-chandler on 2014-12-09
I am trying to setup my brother printer (HL-L2380DW) in Ubuntu 14.04. I have located the drivers but they will not install in 14.04. Should I have to downgrade to 12.04 for the drivers to install? HELP!! Or possibly do I have to get another printer that will work with UBUNTU 14.04.

---

### Post by weatherman2 on 2014-12-09
Brother has drivers for the printer on their website.  You want the Debian (.deb) drivers and NOT the .rpm version.

[http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2380dw_us_as&os=128&dlid=dlf101125_000&flang=4&type3=10033](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2380dw_us_as&os=128&dlid=dlf101125_000&flang=4&type3=10033)

I see Brother offers two different drivers for your printer: a "Generic LPR Printer Driver" and a "Generic CUPSwrapper printer driver."  Both are Debian packages.  It looks like you are supposed to install both of them.

There are instructions on the Brother download page (you need to open a terminal) to install each of them, using the dpkg command.

---

### Post by kurt18947 on 2014-12-10
> **weatherman2 said:**
> Brother has drivers for the printer on their website.  You want the Debian (.deb) drivers and NOT the .rpm version.

[http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2380dw_us_as&os=128&dlid=dlf101125_000&flang=4&type3=10033](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2380dw_us_as&os=128&dlid=dlf101125_000&flang=4&type3=10033)

I see Brother offers two different drivers for your printer: a "Generic LPR Printer Driver" and a "Generic CUPSwrapper printer driver."  Both are Debian packages.  It looks like you are supposed to install both of them.

There are instructions on the Brother download page (you need to open a terminal) to install each of them, using the dpkg command.

Right, and I believe you should install the LPR driver first.  I haven't needed to do the 'before you install' stuff on 14.04.  Another option that I've had good luck with is to use Brother's installer. It must be run from an account with SUDO privileges. It can be found here:

[http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp115c_eu_as&os=127&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp115c_eu_as&os=127&dlid=dlf006893_000&flang=4&type3=625)

The listed printer is DCP-115C but you should be able to change that to your printer model easily.

Edit:  I re-installed a Brother printer trying to use the older Brother installer, ver. 1.0.??.  Didn't work, couldn't find the printer model.  I KNEW I typed it right.  Tried the new isntaller ver. 2.0.0.1 and it worked as expected.  I'd have preferred the older installer script because it doesn't install the printer AND scanner, just the printer.  The way to install just the printer is to accept the first license but decline the second which installs the scanner.

---

