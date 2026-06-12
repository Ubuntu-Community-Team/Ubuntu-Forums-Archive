---
title: "Problems with Xerox Phaser 4400 on Ubuntu 9.10"
date: 2010-01-19
forum: Hardware
---

### Post by shaggylopez on 2010-01-19
First, I should say. I've been working 16 years with Windows... and about a month with Ubuntu.
Second, I'm from Chile. Here we speak spanish. Sorry if my english isn't good enought.

At the office, we are thinking about changing from Windows XP to Ubunto 9.10, so, my work is to check if there is any problem to make it come true.

At this momment, after a few little problems, I've found a big problem with the printer that is driving me crazy.

We have a Xerox printer (Phaser 4400DT) with two paper trays. This printer use Duplex (print both sides of the paper). Ubuntu offers me 5 different drivers.  The first option (Footmatic/Postscript) print without problems... but... I can't choose which tray to use (this is very important here, because we use 2 diferent qualities of paper) and I can't disable the Duplex. The second option (Footmatic/hpijs-pcl5e) allows me to choose tray and enable/disable Duplex, but the text moves out of the paper (!). The other 3 drivers, and de .PPD file from the Xerox website just restart the printer (yes... I send a printing, and the printer screen blinks and works like I've just turned on the printer.)

What I've tried: 
- Edit the .PPD files trying to mix the two working drivers without success
- Asking to Xerox Chile, they told me to try N2125 Postscript drivers without sucess again

I hope here someone can help me. I've wasted about 2 weeks trying to find a solution other than buying another printer... or forgetting the idea of changing to Ubuntu.

---

### Post by wyliecoyoteuk on 2010-01-19
Have you looked [at this link?](http://www.openprinting.org/show_printer.cgi?recnum=Xerox-Phaser_4400DX)

---

### Post by shaggylopez on 2010-01-20
> **wyliecoyoteuk said:**
> Have you looked [at this link?]("http://www.openprinting.org/show_printer.cgi?recnum=Xerox-Phaser_4400DX")

I've tried with [this drivers]("http://www.openprinting.org/show_driver.cgi?driver=Postscript-Xerox&fromprinter=Xerox-Phaser_4400DX") and after installed the DEB package I've changed the drivers of the printe to "*Xerox Phaser 4400DT , Postscript-Xerox 20090512 (OpenPrinting LSB 3.2)*"... and when I print it restart the printer. Have I done something wrong? should I try with another package? I ain't got time at this momment for experiments, maybe I'll try with other drivers from this page tomorow. Thanks wyliecoyoteuk for this hint. If you have an idea of what's going I hope you let me know.

---

