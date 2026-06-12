---
title: "Xerox Phaser 3635 - CUPS adds 4mm / 11.34pt border and shrinks page - PPD issue?"
date: 2017-12-12
forum: Hardware
---

### Post by ch6574 on 2017-12-12
I have a Xerox Phaser 3635 setup to print via IPP. It works, however CUPS seems to add an extra 4mm / 11.34pt border and shrinks the page ever so slightly.

For example, I create a PDF document with a horizontal line 20mm from the top of an A4 page. Print this out and it will be 24mm from the top of the page. This means printing pre-printed forms breaks!

**Now the confusing thing to me...**

1. I capture the raw postscript ([https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) section "Capturing print job data"), and see the line is 20mm from the top. This is good.
2. I send the raw postscript to the printer using "lpr -P <printer> -oraw dump.ps" and this prints out 20mm from the top. This is also good.

I can see the dump.ps file has a BoundingBox of 0 0 595 842, which is the full size of A4.

My question is what is CUPS doing to add the 4mm border and shrinking the page when printing?

If I look in the printer ppd file I see it has "*PaperDimension A4/A4: "595 842"" and "*ImageableArea A4/A4: "11.34 11.34 583.66 830.66"" which is the same only defined with a 11.34pt offset (as the printer cannot print to the edge of the paper). This is the same size as the extra added whitespace CUPS is adding to the PDF printed to the normal printer queue, but *not* adding when printing it to the "Capture" queue and sending that via raw lpr.

Is there a final filter in CUPS that does something funky here?

N.B. I'm expecting anything in the outer 4mm of the page to be clipped, and not to have the entire document slightly shrunk as is happening.

---

### Post by slickymaster on 2017-12-12
*Thread moved to **Hardware**.*

---

### Post by VMC on 2017-12-12
How about the "scale" option on the properties section. Is it set to "shrink-to-fix" instead of desired size.

---

### Post by ch6574 on 2017-12-12
> **VMC said:**
> How about the "scale" option on the properties section. Is it set to "shrink-to-fix" instead of desired size.

So I tried printing the same PDF from a windows machine, and the Xerox driver there has options to "shrink" or "actual size" and these replicate the output I am getting from CUPS.

I've gone into CUPS and removed all the "Option" entries from /etc/cups/printers.conf (such as "fitplot") and went into the "Job Options" in the printer preferences page and hit "Reset" on them all.

This seems to have fixed it...

---

