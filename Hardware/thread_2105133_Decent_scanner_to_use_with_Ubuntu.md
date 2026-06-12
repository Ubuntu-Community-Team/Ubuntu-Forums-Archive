---
title: "Decent scanner to use with Ubuntu"
date: 2013-01-15
forum: Hardware
---

### Post by UltraAnders on 2013-01-15
I was planning to get a Doxie One, but it seems it's not compatible with Linux. It's a real shame as it gets great reviews.

Can anyone recommend me a decent scanner which is Linux compatible? Ideally something convenient and quick that'll scan A4 and receipts. I don't want to spend much more than the £113 the Doxie costs.

---

### Post by UltraAnders on 2013-01-16
Alternatively, is there any software out there that would process a JEPG in the way the Doxie software does, or like Android Apps such as CamScanner, MDScan or HandyScanner. That is, they detect the edges of the doc and crop, improve the contrast, convert to PDF and upload to a cloud service. :-k

---

### Post by na5h on 2013-01-16
Most "all-in-one" printers/scanners from HP tend to work straight out of the box with Ubuntu. They also start at a very low price. Another pretty good choice of brand is Brother, but you might have to download and install the drivers manually off the Internet.

This all depends on your definition of a "decent" scanner, of course...

---

### Post by kurt18947 on 2013-01-16
At least *some* Canon scanners work 'out of the box'.  We have a Canon 8800F which is plug - n - play.  It appears that the successor Canon 9000F is supported as well.  

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

I have no idea how current this list is.  For instance, the only Brother devices listed are shown as unsupported.  You can google Brother + linux drivers to find a list of Brother machines with linux support.  I can attest that many Brother scanning devices are supported though installation has a couple bumps.  I guess the thing is that Brother scanners are not supported by SANE so they're not listed.  If a machine is not on the SANE list and no mention of linux support on the manufacturer's web site though, I'd be wary.

One piece of software I find useful is gscan2pdf, very useful for archiving printed materials.   I'm not much help for  photo scanning, sorry.

---

### Post by UltraAnders on 2013-01-18
Thanks for the replies. The main thing I want to achieve is document archiving. It'll be receipts and statements mainly. I've converted to online statements where I can. I guess when I say "decent", I really mean "quick". Something with a document feeder seems to best way forward.

I was looking at the Epson WorkForce WF-2530, but that's not Linux compatible. I'll check out HP and Brother.

Have already got a nice small printer, so was keen on just a scanner, but seems I might be out of luck.

---

### Post by agillator on 2013-01-18
I just checked the HP site and it appears they do have stand alone scanners. I don't know the prices. However, the recommendation for an all-in-one printer is a good one. I have owned several HP all-in-ones and will own more. The scanners on them work nicely with XSane. I assume standalone scanners would also work with XSane. If you get an HP product then go to the HP site and download the current HPLIP. Purge the HPLIP Ubuntu installs - it doesn't seem to play well with scanners for some reason - and install the downloaded one. It is easy to install and easy to install your equipment. It should install XSane and all the dependencies for you.

---

### Post by UltraAnders on 2013-01-24
Picked myself up a Genius ColorPage SF-600 as it was listed with basic compatibility. Followed the instruction [here]("http://www.meier-geinitz.de/sane/gt68xx-backend/") and copied the firmware file cism216.fw to the relevant folder. The SF600 will scan, but the output isn't right. It's all grey and the text almost looks embossed. Difficult to describe, so I've attached a corner of a page.

Also tried copying the cism603.fw file, but that doesn't make any difference and the scanner doesn't work with just that firmware file in the gt68xx folder.

The scanner works fine in Windows 8.

Any ideas?!?

---

### Post by sdowney717 on 2013-01-24
Bus 006 Device 002: ID 055f:021c Mustek Systems, Inc. BearPaw 1200 CU Plus

Good since windows hates it now even though windows used to like it.
That means I got it for nothing.

It needs one file to work which exists on the xsane site.

Gives the lists here
[http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)

---

### Post by UltraAnders on 2013-01-27
> **sdowney717 said:**
> Bus 006 Device 002: ID 055f:021c Mustek Systems, Inc. BearPaw 1200 CU Plus

Good since windows hates it now even though windows used to like it.
That means I got it for nothing.

It needs one file to work which exists on the xsane site.

Gives the lists here
[http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)Hi, not sure I follow you here. Are you suggesting I should have got the Mustek scanner instead??

The SF600 is listed with basic SANE support, but it seems like that is wrong. Genius Colorpage SF600 0458:2021 cism216.fw

I've copied the relevant file, but as mentioned, the output in Ubuntu is wrong. lsusb shows:
Bus 004 Device 002: ID 0458:2021 KYE Systems Corp. (Mouse Systems) ColorPage-SF600

---

### Post by CindyP on 2013-01-30
> **UltraAnders said:**
> Can anyone recommend me a decent scanner which is Linux compatible? Ideally something convenient and quick that'll scan A4 and receipts. 

I am looking for something similar and want to use gscan2pdf with a Fujitsu ScanSnap S1500 ([Ubuntu Wiki shows this as compatible]("https://wiki.ubuntu.com/HardwareSupportComponentsScannersFujitsu")) and send the scans to evernote via the email function of gscan2pdf.   Anyone have a setup like this working?

---

