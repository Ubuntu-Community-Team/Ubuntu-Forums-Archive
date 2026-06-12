---
title: "Printer Failure - file size maximum?"
date: 2010-04-21
forum: Hardware
---

### Post by jamesco on 2010-04-21
Hello, 

I'm running 9.10, and am printing to a Citizen CT S300 thermal (receipt) printer. I managed to get it working with the provided Linux drivers by using CUPS and it is indeed printing. However, it seems files don't print if they are around 70kb or bigger, the printer just spits out lines of garbage text and I have to turn it off to stop. 

I believe that when a file is too large the printer driver or Postscript driver is failing. Anyone know how I can find the config that sets the maximum buffer size, and if/how this can be changed and fixed?

*edit* I should note that with Windows it printed large files just fine, which leads me to believe it's CUPS or Postscript specifically.

---

### Post by jamesco on 2010-04-22
Well, gave up on this, the Citizen CT S300 isn't officially supported by CUPS or OpenPrinting, and I don't have the time to dig through all the files to find where these 'media limits' are set! Using a newer thermal printer now..

---

