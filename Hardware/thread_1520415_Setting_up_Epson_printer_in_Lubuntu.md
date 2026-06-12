---
title: "Setting up Epson printer in Lubuntu"
date: 2010-06-29
forum: Hardware
---

### Post by geovino on 2010-06-29
How do I set up an Epson all-in-one printer in Lubuntu? 

I'm used to only HPs and setting up with hiplip. How's it different with an Epson. My client did check the Linux friendly printer list, so I know it should work.

---

### Post by ellgor on 2010-06-30
Hi,

Go to this site "Avasys" and get the  driver for your model, sometimes you may have problems with the scanner, if so, get the Imagescan app from "Avasys", when you get to the download page scroll right down until you see "Iscan or Imagescan deb" which is a completely seperate app  from the full printing package, once downloaded use gdebi to automatically install it, needs a reboot to work properly.  

Regards, Ellgor.

---

### Post by geovino on 2010-06-30
> **ellgor said:**
> Hi,

Go to this site "Avasys" and get the  driver for your model, sometimes you may have problems with the scanner, if so, get the Imagescan app from "Avasys", when you get to the download page scroll right down until you see "Iscan or Imagescan deb" which is a completely seperate app  from the full printing package, once downloaded use gdebi to automatically install it, needs a reboot to work properly.  

Regards, Ellgor.

Thanks, I'll give it a try.

---

### Post by geovino on 2010-06-30
...well the printer worked right away, but I wouldn't scan and I couldn't find the link to Iscan or Imagescan deb. Where are they? Also another file I've installed before is lib-sane. That has worked on my other PC and all in one where the printer worked but the scanner wasn't recognized.

---

### Post by geovino on 2010-07-01
I went to the scanner page:
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

Not sure which model to select since my friends Epson is a MX110. I got I can just try one and see if it can get the scanner to work. 

Is this the only file needed to get the scanner to work? is there another choice?

---

### Post by geovino on 2010-07-03
I found the iscan file for .deb and installed but the scanner still doesn't work. 

I don't want to have to buy another printer/scanner, Is there a way to get the scanner to work on this Epson Stylus NX 110?

---

### Post by ellgor on 2010-07-04
Hi,

If you have installed Imagescan then it should appear in the graphics section of the menu, click on it to start it, if its not, press Alt + F2 together and in the run box that appears type in imagescan and run it from there,
it also needs a reboot to work properly, hope this helps.

Regards, Ellgor.

---

### Post by geovino on 2010-07-04
> **ellgor said:**
> Hi,

If you have installed Imagescan then it should appear in the graphics section of the menu, click on it to start it, if its not, press Alt + F2 together and in the run box that appears type in imagescan and run it from there,
it also needs a reboot to work properly, hope this helps.

Regards, Ellgor.

There's a chance that the scanner part is defective.

At this point I've bought another printer that was recommended, an HP C4795 then I can use hplip and all should work. I will only buy HP printers for Linux from now on.

---

### Post by geovino on 2010-07-04
The HP C4795 installed and ran perfectly. :)

---

