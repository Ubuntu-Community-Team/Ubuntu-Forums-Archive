---
title: "Print to PostScript Printer without Ghostscript prefiltering in Jaunty?"
date: 2009-05-23
forum: Hardware
---

### Post by TeaRexx on 2009-05-23
I have an older and not that fast PostScript capable printer (an Apple LaserWriter Select 360 to be exact). Up to Ubuntu Hardy I could disable "Ghostscript Pre-Filtering" in the printer setup. On Intrepid and Jaunty that seems to be impossible, at least via the GUI.

Is there any way to take Ghostscript out of the loop for application output that is already in PostScript format? Ghostscript pre-filtering tends to increase the size of the stuff that is actually being sent to the printer by an amazingly high factor, which is a big problem with a printer connected via a 19,2 kbps RS-232 link or a ca. 50 kbps traditional parallel port. Printing often takes 5 to 10 Minutes before it even starts, and then another three minutes or so per page. The printer has a perfectly fine original Adobe Postscript interpreter built in, so I don't really see the point of passing stuff through Ghostscript only to blow it up.

I have resorted to letting the applications "print to file" and then to "cat" the result directly to /dev/ttyS0, but that seems hardly like a good solution.

Thanks in advance for any help!

---

