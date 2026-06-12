---
title: "Epson V700 - cannot get to work in IEEE1394"
date: 2008-09-07
forum: Hardware
---

### Post by jamespetts on 2008-09-07
I have recently upgraded a computer from Windows XP Home to Linux. The original scanner connected to that computer, a CanoScan 9900F, is not compatible with Linux, so it has been replaced with an Epson Perfection Photo V700.

The V700 has both USB and IEEE1394 connexions, as the CanoScan 9900F did. The scanner is on a shelf the opposite side of the desk to the computer, and the supplied USB cable will not stretch all the way. The original IEEE1394 cable used with the CanoScan will, however, so I plugged it into that.

However, the scanner is not detected either in XSane or when using sane-find-scanner. XSane seems to think that my DVB (digital terrestrial television) card is a scanner, whereas sane-find-scanner finds two USB "scanners": my printer, and an unnamed device. 

Does the V700 work under Sane with IEEE1394? If so, how do I get it to work? Any information would be much appreciated :-)

---

### Post by olmari on 2008-09-27
I'd like to know this too as I am thinking of getting Espon perfection V700 or V750 myself too.

EDIT: Could you test this if is the solution: [http://ubuntuforums.org/showthread.php?t=822003](http://ubuntuforums.org/showthread.php?t=822003)

---

### Post by jamespetts on 2008-10-01
I managed to get it working in the end by downloading and installing "Image Scan!" for Linux (iScan), which is the driver officially recommended by Epson. See [here](http://www.avasys.jp/cgi-bin/lx/bbs/en/scanner-bbs/hyperbbs.cgi?mode=view;Code=5063) for an explanation of how to install iScan in Ubuntu, and [here](https://bugs.launchpad.net/ubuntu/+bug/208405) for a workaround to a particular problem when installing in recent editions of Ubuntu.

---

