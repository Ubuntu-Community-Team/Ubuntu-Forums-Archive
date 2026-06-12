---
title: "[SOLVED] Printing Broke after installing Intrepid - Help please!"
date: 2008-12-09
forum: Hardware
---

### Post by beasel on 2008-12-09
Hi all,

I have a printing problem that has developed since I installed Intrepid that I hope someone can help me troubleshoot.  We have a very specific issue when printing PDF files (as in printing PDF files to paper -- NOT printing files to PDF....)  The text in them will come out fine but the images do not.  This is the case for pdf files that we have created as well as web-based things such as the USPS prepaid shipping lables, which will not print for us.

The really frustrating part is that both of these worked find in Hoary.  This may seem trivial but my wife's home business uses many types of these files and restarting in Windows is becoming a real pain.

I have an HP LaserJet 1012 which is a non-postscript printer (raster based) running off of the HPLIP driver.  Version 2.8.2 was in Hoary and it is now 2.8.7 in Intrepid.  I tried to uninstall the Intrepid version and install a version of 2.8.2 from a tar.gz I found on the web, but it was no luck (thought I'm not positive I did it correctly.  The print driver in the printer properties says 2.8.2 but it doesn't show up in synaptic or following a dpkg -l command).  I'm not actually sure it's the driver, but I don't know what else it would be.  Maybe a new version of CUPS or Evince?  The files print fine on the same printer in Windows and used to print in Hoary on this printer.  So some new version of something has broken it for me.

Any ideas on how to troubleshoot?  Otherwise this will be a deal-breaker for me for Intrepid and I will be moving back to Hoary....

Thanks for any help possible in advance!

---

### Post by beasel on 2008-12-09
Never Mind -- I could have sworn I tried this in Xpdf as well, which is what originally convinced me it was a printing bug.  But it appears to involve Evince only, so I will go haunt their bug reports or file a new one.

If anyone else has a similar problem in the future, it also seems to be discussed in [bug 273912]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/273912") on Launchpad.

---

### Post by beasel on 2008-12-09
p.p.s.  for others who may stumble upon this and want a solution:

You need to install an upgrade to the libcairo package, which is not in the Intrepid repositories (as of this writing).

Look at [bug report 281713]("https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/281713") for instuructions and more discussion about it.

Yay for the ubuntu (and related) community!

---

