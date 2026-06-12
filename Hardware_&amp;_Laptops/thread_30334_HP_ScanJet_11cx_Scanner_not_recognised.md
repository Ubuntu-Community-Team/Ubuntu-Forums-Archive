---
title: "HP ScanJet 11cx Scanner not recognised"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by Sarah Bartlett on 2005-04-28
Hello 

I have just installed Hoary 5.04: everything has been configured & installed except for my SCSI ScanJet 11cx.  Hoary 5.04 has picked up the Tekram SCSI card, but Sane OCR software doesn't know that I have a scanner attached.  I have seen documentation at [http://www.sane-project.org/man/sane-hp.5.html](http://www.sane-project.org/man/sane-hp.5.html) that indicates that the the ScanJet 11cx scanner will work with the sane-hp library.

Trouble is, because I am so new to Hoary 5.0.4, I haven't a clue as to whether the sane-hp library is installed, if it isn't then how to install it & where to get it: if it is installed, then how to set-up the scanner etc.

Can some kind person out there give me a step-by-step idiots guide to sorting this out?

Any help much appreciated

Cheers, Sarah

---

### Post by Psquared on 2005-05-05
Sarah, you need gocr and a program called "quiteinsane". I have not tried them but they are in the repos - probably "universe." I found them in Synaptic.

(You apparently already have sane and xsane)

---

