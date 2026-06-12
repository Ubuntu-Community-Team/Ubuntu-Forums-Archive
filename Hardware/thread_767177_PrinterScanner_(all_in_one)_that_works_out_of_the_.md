---
title: "Printer/Scanner (all in one) that works out of the box?"
date: 2008-04-25
forum: Hardware
---

### Post by Vega on 2008-04-25
Hello everyone,

I was curious to know what's a really good printer/scanner (all in one) that will work with Hardy Heron right out of the box

If y'all have any suggestions I would love to read them

As usual, ty

---

### Post by RichardG891 on 2008-04-26
I have a Brother DCP-115C. Dirt cheap but does reasonable borderless photos; and routine printing/scanning fine. Brother's website holds your hand through the install but couldn't get it to install their lpr and cupswrapper with Hardy (worked fine with Gutsy and Feisty)... However, the packages you need are in the standard repositories ("brother-cups-wrapper-extra"), and synaptic sets it up automatically.... you need to use the driver for the MCF210c. Had no problems. The scanner needs one package installed (brscan2) (and you can install a second one to intercept the quick "scan" button on the device), and modify one line in fstab - The manufacturer's instructions are very straightforward.

---

### Post by nhandler on 2008-04-26
From my experience, most HP printers will work out of the box with Ubuntu. I have an HP Photosmart C5180 All-in-One. Hardy detected it the instant I connected it, and then it configured it automatically. HP printers have been supported by Ubuntu for some time now, and as a result, most will work great out of the box.

Prior to my HP printer, I had a Brother DCP-110c, and I could not get this to properly work with Ubuntu (Gutsy). However, it looks like Ubuntu has improved support for Brother printers since then.

---

### Post by linuxwizard on 2008-04-26
Read over this > [http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters](http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters)

---

