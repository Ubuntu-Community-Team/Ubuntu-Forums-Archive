---
title: "xsane -- Failed to start scanner: Invalid argument."
date: 2008-10-11
forum: Hardware
---

### Post by moonguide on 2008-10-11
What do I need to read to learn how to get my Epson Perfection 600 scanner working on 8.04? This machine used to run SuSE 10.0. I had this scsi scanner working on that distro.

I powered up the scanner. When I ran xsane I got the error message telling me that it couldn't find a scanner. (I expected this.) Using Synaptic, I installed scsitools. I ran rescan-scsi-bus.sh and then ran xsane again. Now it finds the scanner, but when I try to "Acquire preview" I get the error message: Failed to start scanner: Invalid argument.

I've tried running xsane with strace, but I get a 47,000+ line output file, and don't really know what I'm looking for; the above error message is not found in the strace output file.

Recommendations on what to do next are appreciated.

---

