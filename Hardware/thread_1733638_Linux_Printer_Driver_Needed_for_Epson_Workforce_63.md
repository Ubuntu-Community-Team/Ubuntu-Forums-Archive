---
title: "Linux Printer Driver Needed for Epson Workforce 635"
date: 2011-04-19
forum: Hardware
---

### Post by beadedbytes on 2011-04-19
I found the following printer driver file on the following website:

Printer driver website (w/o quotemarks):  
"http://gamblis.com/2010/11/03/epson-workforce-633-driver-for-ubuntu-linux/"

Printer driver file (w/o quotemarks):
 "epson-inkjet-printer-workforce-635-nx625-series_1.0.0-1lsb3.2_i386.deb"


When I attempted to open/run inside the Ubuntu Software Center, the following message appeared:  Wrong Architecture 'i386'.


What does this message mean?  Is there a workaround?  Also, is there a different driver for Linux that I should use?


Thanks in advance for any help!

---

### Post by Rudio on 2011-05-06
p { margin-bottom: 0.08in; }  I'm trying to get an NX625 working and I tried the _i386.deb version and also got the same message using the Software Center. When I tried command line (if I recall correctly) it said I should go for the _amd64.deb download. Anyway that worked for printing. I'm still having trouble with the scanning. I downloaded from the Avasys site. Since I've an Intel CPU don't know why it should be _amd.

---

### Post by beadedbytes on 2011-05-07
As mentioned in General Help, the scanning feature on my Epson Workforce still does not work in Ubuntu 10.10.

I found the following info about the scanner driver file that I have not been able to make operational.

_Website:_
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

_Scanner driver:_
iscan_2.26.3-1.ltdl7_amd64.deb  (I also tried other *.deb files, but did not find one that worked.)

Documentation about installation:
See "Installation Method" on the same website; file called "userg_revL_e.pdf".  See Chapter 4.  There's a paragraph that says the following --
Please note that scanning over the network is only supported in a client/server setup. Scanners directly attached to the network are not supported.

Let me know if you have any success.  Cheers.

---

### Post by happynix on 2011-09-03
Apparently  Epson in Japan in not afraid of linux

Scanner Drivers
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

Printer Drivers
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)

---

