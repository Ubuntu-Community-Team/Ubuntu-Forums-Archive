---
title: "Lexmark printer never fails the same way twice"
date: 2008-08-26
forum: General Help
---

### Post by AngusM on 2008-08-26
Before I posted a problem with printing that had it not being able to process a "Raster". Now the print manager hangs for a while in the "processing" state, then puts and endless amount of these in my /var/log/cups/error_log:
D [26/Aug/2008:20:36:26 -0400] [Job 30] cups->header.Duplex = 0
D [26/Aug/2008:20:36:26 -0400] [Job 30] cups->page = 1
D [26/Aug/2008:20:36:26 -0400] [Job 30] cupsPPD = 0x81965a0
D [26/Aug/2008:20:36:26 -0400] [Job 30] cupsPPD->flip_duplex = 0
D [26/Aug/2008:20:36:26 -0400] [Job 30] width = 4800, height = 6258
D [26/Aug/2008:20:36:26 -0400] [Job 30] PageSize = [ 612 792 ], HWResolution = [ 600 600 ]
D [26/Aug/2008:20:36:26 -0400] [Job 30] HWMargins = [ 18.000 36.000 18.000 5.000 ]
D [26/Aug/2008:20:36:26 -0400] [Job 30] matrix = [ 8.333 0.000 0.000 -8.333 -150.000 6558.333 ]
D [26/Aug/2008:20:36:26 -0400] [Job 30] GPL Ghostscript 8.61: DEBUG2: cups_get_matrix(0x809ea3c, 0x82ed98c)

I have the z600cups driver installed.

---

