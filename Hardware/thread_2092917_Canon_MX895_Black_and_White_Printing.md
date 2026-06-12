---
title: "Canon MX895 Black and White Printing"
date: 2012-12-09
forum: Hardware
---

### Post by SirLouen on 2012-12-09
I've been trying both drivers for this printer, Ubuntu default (MX890) and Canon specific IJ Printer Driver 3.70.

Default driver can print Black and White, but takes too long to print, seems like it has to print the whole page in a greyscale system, even white spaces are being printed. 

The IJ Printer Driver works fine, but doesn't give me the option for B&W printing, just color mode.

Anyone has this printer (or similar and has find a solution to this?)

---

### Post by SirLouen on 2012-12-09
Googling a little bit, I've found an option inside the Properties section in the printer. Into Job Options, Advanced section if I put a property called "CNGrayscale" to TRUE then all the jobs will be printed in Greyscale, and if I set it back to FALSE then all will be printed in Color. 

But for example if I'm printing a PDF file I cannot set this directly, I should be doing the whole configuration thing all the time.

Any ideas on how to make this easier?

---

