---
title: "Ubuntu 20.04 and Canon lide 400 scanner not working with Scangearmp2"
date: 2020-04-25
forum: Hardware
---

### Post by valmatej on 2020-04-25
Hi,
I have a problem with my scanner Canon Canoscan lide 400,is showing up in "lsusb" I have installed Scangearmp2 from Canon´s website version 3.70 but after opening this up, tell me "Cannot find available scanners.",but scanner is plugged in and with Ubuntu 19.10 works perfectly out of the box with Scangearmp2.
Please help me.

---

### Post by TheFu on 2020-04-25
Have you contacted Canon for help?  Do they have an ETA for supporting 20.04?

---

### Post by valmatej on 2020-04-26
Yes,but they haven't answered yet. I don´t know what is "ETA" means.Sorry.

---

### Post by CelticWarrior on 2020-04-26
[https://en.wikipedia.org/wiki/Eta_(disambiguation)](https://en.wikipedia.org/wiki/Eta_(disambiguation))

Of course, in this context, it means figuratively [https://en.wikipedia.org/wiki/Estimated_time_of_arrival](https://en.wikipedia.org/wiki/Estimated_time_of_arrival)

---

### Post by valmatej on 2020-04-27
Canon support: they didn´t help me, because they sent link to linux driver download website. They haven´t any information of newer versions of their software. :( 
I don´t know what next.

---

### Post by TheFu on 2020-04-27
> **valmatej said:**
> Canon support: they didn´t help me, because they sent link to linux driver download website. They haven´t any information of newer versions of their software. :( 
I don´t know what next.

Let me tell a story ... 

My mother had a great Canon photo printer.  Linux drivers for it were sold by a company in Europe for $50.  At the time, a new Laser printer that was fully Linux supported and worked extremely well was $55, so she wouldn't be stuck paying $40/yr for new ink or fighting with drivers every few years.  Laser printer toner lasts years.  So, rather than pay for the drivers, we sold the Canon printer and bought a cheap laser that had built-in Linux support without hinting for any drivers.  
That was around 2010.  Mom died after a very long life, but that laser printer is still going, hassle free, on a $22 2nd toner cartridge rated for something like 15K pages - might be 8K pgs. I don't know. It is still USB connected to a Linux print server (I don't do network printers).  The laser printer IS NOT from Canon.

For a scanner, I gave away an huge Epson Page Scanner when Linux drivers weren't available and picked up a $60 Brother All-in-One 240C with a sheet feeder. That must have been around 15 yrs ago.  The specific model Brother was, and is, well supported by Linux.  When the ink ran out (well, it actually dried up), I never replaced it.  To me, it was about the sheet-feed scanning and fax capabilities.  The govt here still uses faxes for a number of business things where signatures are necessary.  The last thing I want my interactions w/ the govt to be is through email or telephone. I'm odd that way.

I realize that doesn't help you with the Canon, but avoiding problems is a good technique too.
[https://www.theregister.co.uk/2020/04/28/hp_ink_officejet_drm/](https://www.theregister.co.uk/2020/04/28/hp_ink_officejet_drm/) Cautionary tale about having network connected devices.

---

### Post by rbmorse on 2020-04-27
The pay to play scanner front end VueScan ( [https://www.hamrick.com/](https://www.hamrick.com/) ) lists the Canon LiDE 400 as supported hardware.  

I use it with my LiDE 220 at present, and with a series of older Epson flatbeds going back at least ten years.  It is high quality software and well supported.  The license fee is modest and well worth it, in my opinion. You can try it at no cost to ensure compatibility/suitability, but it leaves a watermark on the output until licensed. 

Another thing to try is the free, from repository, simple-scan.  it's listed as "document scanner" in the Ubuntu Software catalog, but synaptic/apt find it as simple-scan.  It's rudimentary, but works fine for quick jobs with my 220 and may pull in the correct SANE support library for your 400.  You can always delete it if it doesn't work.

---

### Post by valmatej on 2020-04-28
matej@matej-desktop:~$ scanimage
Output format is not set, using pnm as a default.
Error my backend :    out of memory
scanimage: open of device pixma:04A91912 failed: Device busy
matej@matej-desktop:~$

---

### Post by vamento on 2020-07-13
Hey I had the same issue with "device busy" and found a solution on [https://techprpr.com/ubuntu-howto-install-canon-lide-300-400-on-ubuntu-18-04/](https://techprpr.com/ubuntu-howto-install-canon-lide-300-400-on-ubuntu-18-04/):
```
sudo apt remove ippusbxd
```

LiDE 400 now works perfectly as before.

---

### Post by valmatej on 2020-08-15
Hello, big thank you so much,it is working perfectly.
Thank you all.

---

### Post by brian_p on 2020-08-15
You are connected by USB?

Please give what you get for ```
lsusb -v | grep -A 3 bInterfaceClass.*7
``` ```
systemctl list-units "ippusbxd*" | grep service
``` ```
scanimage -L
```

---

