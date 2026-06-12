---
title: "Scanner problem - Scanjet 4850 on Ubuntu 16.04"
date: 2017-12-03
forum: Hardware
---

### Post by phil215 on 2017-12-03
I'm attempting to use my trusty old HP Scanjet 4850 on a computer running Ubuntu 16.04.
 So far this has proved to be something of a problem and now I'm stuck.
 
 The application gscan2pdf appears to work, because the lamp can be seen scanning under a test
 document, but the final image is completely black.
 The other application, XSane, scans and then promptly crashes.
 
 It would be good to hear from anyone who is successfully using the same or similar hardware on this Linux distribution.
 If the only way is to invest in scanning software, then I would be interested to read reviews first.
 My aim is to have something equivalent to ScanSoft's PaperPort on Ubuntu, if possible.

---

### Post by jasomux on 2017-12-04
First things first; the fact that the scanner lights up and scans tells us the scanner is recognized by the system, so there's hope. I looked up this scanner on the sane-project.org site and found a listing for an HP Scanjet 4850C, not a 4850, using the built in "genesys" driver. Here's the link to that page:

[http://sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)

I had similar problems with my Cannon flatbed scanners at first because they are USB 2.0 like yours and they did not work correctly if plugged into a USB 3.0 port. Even though USB is supposed to be backward compatible, my scanner would freeze up after scanning one page and not return to the "ready" state when using a USB 3.0 port. Sometimes the software would crash also. So check which type of USB port you're using and plug into a 2.0 port.

I've read that the latest versions of Xsane have been very buggy, so forget that option. I haven't tried using gscan2pdf, but if you want to scan images or multiple page PDFs you can use simple-scan. Don't let the name fool you; it's a pretty comprehensive tool.

If you want to see how your system recognizes your scanner, open a terminal and type:

```
scanimage -L
```

Here's the result for my Cannon scanner:

```
device `genesys:libusb:001:010' is a Canon LiDE 210 flatbed scanner
```

If your output looks similar with "genesys" and your scanner name, it should be using the built in driver. If that all looks good, I would try using simple-scan. It may already be installed on your system by default. Look for it in Applications > Graphics. if not, open a terminal and type:

```
sudo apt install simple-scan
```

That's my two cents. Best of luck.

---

### Post by slickymaster on 2017-12-04
*Thread moved to **Hardware**.*

---

### Post by SeijiSensei on 2017-12-04
I have a 4850 and have never been able to get it to work with Ubuntu and free software.  I ended up buying a copy of [VueScan](https://www.hamrick.com/) which works just fine.

---

### Post by phil215 on 2017-12-06
Thank you for your replies jasomux and SeijiSensei, they are very helpful.
 Apologies for the delay in getting back, but I've been preoccupied with a demanding GRUB problem, which is now happily resolved.
 I can now run the scanner on a legacy system, which will suffice for the time being.
 

 The scanner's built-in device driver is showing on my system and there are no USB 3.0 ports.
 I shall give simple-scan a try, but long-term I'm not looking for a command line solution.
 It looks like my best option will be to invest in a copy of VueScan.

---

### Post by jasomux on 2017-12-07
phil215, simple-scan is a full GUI program, not a command line tool; I just gave the command for installing it because it's quicker than using the software center. Anyway, judging by SeijiSensei's experience, looks like VueScan may be your only option. Best of luck.

---

### Post by phil215 on 2017-12-07
Thanks for that jasomux, yes, I see that it's a GUI program now. I'll give it a try and see what the results are like.

 

 I note that with almost 13k beans, SeijiSensei has surely achieved Guru status.
 If he gave up on the free software, then it could mean that I'll eventually have to pay for Ubuntu software. For me that will be a first!

---

### Post by SeijiSensei on 2017-12-07
There are lots of scanners that work just fine with Linux and free software, just not this particular device.  It was given to me so paying for VueScan was cheaper than buying a scanner on my own!  If I were buying a new scanner, I'd stick to ones listed in the [SANE database](http://www.sane-project.org/sane-supported-devices.html).

> **phil215 said:**
>  I note that with almost 13k beans, SeijiSensei has surely achieved Guru status.!

Thank you, young padawan!  Age (68) and experience with Linux (>25 years) does have some value, I guess.

---

### Post by phil215 on 2017-12-09
Thanks for providing the link SeijiSensei.
 Re. your scanner - it's always good to receive free (good quality) hardware!
 A few years ago a friend donated a couple of inkjet printers. They took some time to refurbish, but they were well worth the effort.

 

 Now that the scanner is working on a legacy O/S and I have dual-boot configured, an upgrade is not a high priority, at the moment. However, if in the future I do upgrade the scanner, I shall certainly refer to the compatible hardware list.

---

