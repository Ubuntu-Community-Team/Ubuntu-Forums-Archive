---
title: "Solved - scanning issue with Canon Pixma MG3220"
date: 2016-12-18
forum: Hardware
---

### Post by drumkitcat on 2016-12-18
Hi everyone,
just wanted to share this if you've experienced the same problem I've had with the Canon Pixma printers... note I'm using Ubuntu Studio 16.10

1. This is a wireless network printer, so I can easily add it to my available printers as a network printer wirelessly.

2. the problem up to now, has been that while I can print to the printer wirelessly, I cannot get the SimpleScan program to detect it to scan anything.

3. Solution:  luckily in this case, the printer is in the same room as my desktop computer running Ubuntu Studio - 
3.1 I connected the USB cable from the printer to the desktop computer 
3.1 I went into the CUPS interface to reconfigure the driver for the Canon MG3200 series using the enhanced Gutenprint driver (highly recommended!) from Sourceforge
3.2 with the USB cable connected to the computer, SimpleScan was able to scan a document from the Canon Pixma printer - first time ever!  Previously I was getting an error stating "no scanner found" - so it can't scan wirelessly although, I can use that printer to scan wirelessly from a Windows 7 computer I have in the basement; but that's another story.

Basically, if you can connect a USB cable to the printer and your computer, you'll be able to scan directly.

I just finished setting up my Canon CP510 Selphy using the Gutenprint drivers through CUPS so at the same time I set up the exact Gutenprint driver for the Pixma MG3220 printer I have.

Hope this works for you!

---

### Post by mörgæs on 2016-12-18
Thanks for an attempt at marking the thread solved. 
If you use Thread Tools there is a better chance that people will find it.

---

### Post by drumkitcat on 2016-12-19
Thanks, I'm new to this - I'll update the thread as solved using the thread tools.

---

