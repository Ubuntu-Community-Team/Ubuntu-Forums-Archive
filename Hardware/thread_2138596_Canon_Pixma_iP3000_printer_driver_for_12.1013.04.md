---
title: "Canon Pixma iP3000 printer driver for 12.10/13.04"
date: 2013-04-24
forum: Hardware
---

### Post by sdgiffin on 2013-04-24
Recently ditched Windows completely and went "pure Ubuntu." Problem is, now I can't print. Google has not been kind to me while looking for a suitable Canon printer driver for use on Ubuntu 12.10/13.04 and Canon says they don't officially support the Pixma iP3000 in Linux. Does anybody know where I can find a passable driver that will support my printer? I'm unemployed currently and need my printer for printing resumes, and can't afford to buy a replacement printer that's "Linux certified" by the manufacturer.

---

### Post by pdc on 2013-04-24
this thread 

[http://ubuntuforums.org/showthread.php?t=2036453](http://ubuntuforums.org/showthread.php?t=2036453)

reports that gutenprint worked for *beoram*

[http://www.openprinting.org/driver/gutenprint/](http://www.openprinting.org/driver/gutenprint/)

aikishugyo who was in the post #2 maintains the gutenprint I believe so he is a real expert on it 

......that should get you going; let us know how you do .......

you can see there are dedicated packages for both .deb and .rpm

(Ubuntu uses .deb packages by the way.........) and there are also 32bit and 64bit packages...........

I believe ubuntu uses the LSB 3.2

---

### Post by hkphooey on 2013-04-25
Probably not what you were looking for, but the turboprint driver will fix you up for about USD 37. Well its cheaper than buying a new printer ... 
[http://www.turboprint.info/](http://www.turboprint.info/). I tried to get a Canon printer working at a client's office, and that's what I came up with for them. At the end of the day you have to put a price on your time. If you spend a whole day messing about with drivers and fixes, then do you value your day at more than 37 USD? If you have lots of time, perhaps not. 

I'm not associated with the company in any way. I wish Canon would just buy them out and release the tech for free in fact ... I've pretty much stopped buying Canon printers these days.

---

### Post by aikishugyo on 2013-04-25
Hi there,
As pdc writes, I currently help to maintain the Canon backend of the gutenprint inkjet driver package.
And yes, the iP3000 is supported. How well depends on your expectations:
1) Text: Black and white should be perfect. Color might not be perfectly calibrated, but acceptable.
2) Photo printing: this is iffy, since calibration quality is unknown and requires user feedback and interaction to fix. If you find the current default color calibration acceptable, please let us know.
The gutenprint mailing list is a good place to post questions about the driver. Here is the website, from whence you can get the mailing list information:
[http://gimp-print.sourceforge.net/]("http://gimp-print.sourceforge.net/")

Best regards,
Gernot Hassenpflug

---

