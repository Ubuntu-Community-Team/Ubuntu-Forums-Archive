---
title: "Need the community to pay some attention to my scanner (please please)"
date: 2022-11-30
forum: Hardware
---

### Post by jonfisher on 2022-11-30
Ever since I upgraded to Ubuntu 22.04.1 LTS, my HP printer/scanner combo simply won't recognize the scanner part of the printer.  It's the HP Laser Jet Pro MFP M127fn combo.
 
What concerns me the most is that several previous long term releases simply recognized the scanner & worked flawlessly.  

I've tried various scanner apps, and know it's not the apps failing me.
 
I've posted here and several other Linux forums over the past 6 months, or so, with no solution in site.

Now I don't use my scanner very often, but when I need to use it, well, it's just not usable at all. 
 
I would really like the community to pay me some extra attention and help me fix this.  I'm willing to try uninstalling/reinstalling to try to get this scanner to work again.  This is one of the few times that I've really been frustrated with my computer.
 
Please please please help.....

Addendum:  One person messaged me with this possible solution (which may be a pay for solution).  Is this perhaps my only recourse ?    link:  [https://www.hamrick.com/](https://www.hamrick.com/)

---

### Post by #&amp;thj^% on 2022-11-30
well if you want to include this it might help:
```
 dpkg -l | grep sane
```

---

### Post by QIII on 2022-11-30
Don't use that link and don't download anything.  Dollars to doughnuts it's a scam.

---

### Post by Holger_Gehrke on 2022-11-30
@QIII: hamrick.com are the authors of vuescan, a well-known and respected commercial program available for Linux and Windows that is often the last recourse when scanner manufacturers don't offer new drivers for old models. So no, it's not a scam; too bad I don't have any doughnuts to cash out your bet ...

@jonfisher: another package besides sane (**S**canner **A**ccess **N**ow **E**asy) that you might need is hplip (HP Linux Imaging and Printing), which should give you a sane-backend for HP All-in-One devices.

Holger

---

### Post by TheFu on 2022-11-30
> **Holger_Gehrke said:**
> @QIII: hamrick.com are the authors of vuescan, a well-known and respected commercial program available for Linux and Windows that is often the last recourse when scanner manufacturers don't offer new drivers for old models. So no, it's not a scam; too bad I don't have any doughnuts to cash out your bet ...


+1.  When my mother's cheap all-in-one didn't work with Linux, the choice was to buy a new, supported, all-in-one or to pay $50 for the drivers from Hamrick.  At the time, a new all-in-one was $75 and we'd looked up that it would "just work" with Linux.  I recommended she give away the old one to someone in the family using Windows and buy new.  Two people were made happy that day.

My next all-in-one will support
a) driverless printing  
b) driverless scanning (part of the IPP standard now) with the ability to scan directly to USB or SDHC storage - no computer needed.

Life is too short to deal with stupid stuff like this more than a few hours when $80 makes the problem go away for ever.  Just sayin'.

Maybe this link will help: [https://snapcraft.io/ipp-usb](https://snapcraft.io/ipp-usb) . I don't know, as I've never used it with my 2008 (and older) printers or scanner. It is a snap package, but there are required things that must be done before and after the snap is installed to prevent collisions. At least that's what I'm reading.

---

### Post by QIII on 2022-11-30
> **Holger_Gehrke said:**
> too bad I don't have any doughnuts to cash out your bet ...

I'll get you a dozen the next time I go to the bakery ...

---

### Post by CharlesA on 2022-11-30
> **QIII said:**
> Don't use that link and don't download anything.  Dollars to doughnuts it's a scam.

I found that particular software was recommended when I was looking to digitize photos with a flatbed scanner, but I haven't tried it myself.

I wouldn't use it to solve this issue, however.

---

### Post by jonfisher on 2022-12-01
> **TheFu said:**
> +1.  When my mother's cheap all-in-one didn't work with Linux, the choice was to buy a new, supported, all-in-one or to pay $50 for the drivers from Hamrick.  At the time, a new all-in-one was $75 and we'd looked up that it would "just work" with Linux.  I recommended she give away the old one to someone in the family using Windows and buy new.  Two people were made happy that day.

My next all-in-one will support
a) driverless printing  
b) driverless scanning (part of the IPP standard now) with the ability to scan directly to USB or SDHC storage - no computer needed.

Life is too short to deal with stupid stuff like this more than a few hours when $80 makes the problem go away for ever.  Just sayin'.

Maybe this link will help: [https://snapcraft.io/ipp-usb](https://snapcraft.io/ipp-usb) . I don't know, as I've never used it with my 2008 (and older) printers or scanner. It is a snap package, but there are required things that must be done before and after the snap is installed to prevent collisions. At least that's what I'm reading.

This black and white HP laser printer has been a real work horse.  I want to try to keep it.  I just don't understand why this new LTS version of Ubuntu has rendered the scanner useless after so many years of working service....  IMO, it's not the printer/scanner combo that is the issue, it's something inherent in this LTS version....

p.s. I will try some of the solutions in this thread.......

---

### Post by jonfisher on 2022-12-01
michael@michael-HP-EliteDesk-800-G1-SFF:~$ dpkg -l | grep sane
ii  libcommon-sense-perl:amd64                     3.75-2build1                              amd64        module that implements some sane defaults for Perl programs
ii  libkf5sane-data                                21.12.3-0ubuntu1                          all          scanner library (data files)
ii  libkf5sane5:amd64                              21.12.3-0ubuntu1                          amd64        scanner library (runtime)
ii  libsane-common                                 1.1.1-5                                   all          API library for scanners -- documentation and support files
ii  libsane-hpaio:amd64                            3.21.12+dfsg0-1                           amd64        HP SANE backend for multi-function peripherals
ii  libsane1:amd64                                 1.1.1-5                                   amd64        API library for scanners
ii  sane-airscan                                   0.99.27-1build1                           amd64        SANE backend for AirScan (eSCL) and WSD document scanner
ii  sane-utils                                     1.1.1-5                                   amd64        API library for scanners -- utilities
ii  xsane                                          0.999-11ubuntu1                           amd64        featureful graphical frontend for SANE (Scanner Access Now Easy)
ii  xsane-common                                   0.999-11ubuntu1                           all          xsane architecture independent files
michael@michael-HP-EliteDesk-800-G1-SFF:~$

---

### Post by TheFu on 2022-12-01
> **jonfisher said:**
> This black and white HP laser printer has been a real work horse.  I want to try to keep it.  I just don't understand why this new LTS version of Ubuntu has rendered the scanner useless after so many years of working service....  IMO, it's not the printer/scanner combo that is the issue, it's something inherent in this LTS version....

p.s. I will try some of the solutions in this thread.......

I completely understand. It is frustrating when stuff that has been working for years stops working.  HP used to be very good at this, but even inside companies, things change, priorities change.

Most laser printers support IPP, so it should still print fine.  Scanning has always been a little harder, IME.  My $60 laser printer from 2007-ish has been working all this time.  The company sold their printing business to someone else a few years ago, but my laser doesn't care. It keeps working.  I've changed the toner twice in all these years - printing is something I seldom do.  The last 2 yrs, I shake the toner around to get more even coverage on the page.  

When it breaks, hopefully, after the next toner spare (which I've had in a closet for 5+ yrs) is nearly done, it will be time to replace 2 devices with a single laser + all-in-one that do driverless printing and scanning.  I figure that will be in 10 yrs.

Code is changed all the time.  Sometimes that breaks other software.  Did you open a bug in Landscape?  If not, nobody can do anything except provide suggestions to work around the problem.  And bugs with only 1 report are unlikely to get any developer time, beyond being sent to the upstream project.  For scanners and printers, they will spend the most time on the most popular devices, so our older devices won't get much love, unless someone on the project development team has one too.

---

### Post by jonfisher on 2022-12-01
Well, I have an HP laptop.  I will plug the printer up to it and see if the scanner performs on it.  If so, then we can begin to eliminate variables here....

---

### Post by jonfisher on 2022-12-01
OK, I connected the printer/scanner combo to the hp laptop, installed several more scanner programs on it, and it wouldn't get the scanner to work either.
So, basically, I just have a working printer.  
I may buy a little stand alone scanner on the cheap.  any recommendations (new or used)....   p.s. i've always been partial to hp branded items....   It's mom's computer - she authorized a $20 and less purchase off of ebay.  If anyone can recommend a usb hp from ebay I'd appreciate it....  aS i SAID, i rarely scan, but every 6 months or so i need to do a copy or 2
Addendum:  $30 would be ok price too & if shipping is $10 or less also
aDDENDUM 2: HOW ABOUT THIS ONE.  also need it to scan standard size paper:  [URL="https://www.ebay.com/itm/385083293115?_trkparms=amclksrc%3DITM%26aid%3D1110013%26algo%3DHOMESPLICE.SIMRXI%26ao%3D1%26asc%3D20201210111452%26meid%3D0424445c095b47fa867921372c97e86d%26pid%3D101196%26rk%3D4%26rkt%3D10%26sd%3D385083293115%26itm%3D385083293115%26pmt%3D1%26noa%3D0%26pg%3D2047675%26algv%3DPromotedRVI%26brand%3DHP&_trksid=p2047675.c101196.m2219&amdata=cksum%3A3850832931150424445c095b47fa867921372c97e86d%7Cenc%3AAQAHAAAA4Iq9Pd1eiueKRlho1pRz6mJRDvgr0WCiGMCLOrPg1WkM2D%252BnUk9nbLo1b%252F7%252Fb1f5on55H7ND7hAjneLWVvOV0Kzv85MRywrOkMuNf%252FTIBDyf%252F7OcrkAexOhDMIQ5qHGR70W5bAZPlj5zxO3KuqzzhW4KUd0DHBEsD1qINQIiSD6njmkUwmvcS75b9QT1lQ4ArCXQ62QMauaj3qiTEeLS7mRUMWS8BE1QB0l96jjaSkx%252F00WniSYAPlZcXYqC3Fr7pkFreMtk4hOwy%252FVZG7dcFMJBcSn23xI3Cw5s%252BLA7aWMr%7Campid%3APL_CLK%7Cclp%3A2047675&epid=22056763877"]https://www.ebay.com/itm/385083293115?_trkparms=amclksrc%3DITM%26aid%3D1110013%26algo%3DHOMESPLICE.SIMRXI%26ao%3D1%26asc%3D20201210111452%26meid%3D0424445c095b47fa867921372c97e86d%26pid%3D101196%26rk%3D4%26rkt%3D10%26sd%3D385083293115%26itm%3D385083293115%26pmt%3D1%26noa%3D0%26pg%3D2047675%26algv%3DPromotedRVI%26brand%3DHP&_trksid=p2047675.c101196.m2219&amdata=cksum%3A3850832931150424445c095b47fa867921372c97e86d%7Cenc%3AAQAHAAAA4Iq9Pd1eiueKRlho1pRz6mJRDvgr0WCiGMCLOrPg1WkM2D%252BnUk9nbLo1b%252F7%252Fb1f5on55H7ND7hAjneLWVvOV0Kzv85MRywrOkMuNf%252FTIBDyf%252F7OcrkAexOhDMIQ5qHGR70W5bAZPlj5zxO3KuqzzhW4KUd0DHBEsD1qINQIiSD6njmkUwmvcS75b9QT1lQ4ArCXQ62QMauaj3qiTEeLS7mRUMWS8BE1QB0l96jjaSkx%252F00WniSYAPlZcXYqC3Fr7pkFreMtk4hOwy%252FVZG7dcFMJBcSn23xI3Cw5s%252BLA7aWMr%7Campid%3APL_CLK%7Cclp%3A2047675&epid=22056763877

(could even offer less on this one & i like when buyers offer 30 day return option)

Addendum 3:  No power cables come with this scanner, so I guess this particular one is a no go

[/URL]

---

