---
title: "Printer not working"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by ellis rowell on 2007-11-02
I have been using an Epson Stylus C680 with CUPS for sometime, it worked extremely well with v7.04 and I have now updated to V7.10. I installed Turboprint and in trying to use the C680 with that it seems that the CUPS has now reverted to Generic and I cannot get it back to CUPS. Where do I go from here?

---

### Post by myoungf1 on 2007-11-02
I am having the same problem with an epson stylus color 640.  It worked great in feisty but now doesn't work at all in gutsy.  Also my epson diagnostic tools also do now work any longer.

Update:  I did some searching and found that in a terminal if you type tail /var/log/cups/error_log you can watch for errors.  What I found after trying to print a test page was that when trying to access /dev/lp0 there wasn't sufficient permissions to open the printer.  After I chmod'ed the /dev/lp0 the printer started working like a charm.

---

### Post by ellis rowell on 2007-11-02
I hope you get yours sorted out. I struggled with mine for some time to no avail, then after the computer had been switched off for a while I started it up and it worked OK. V-e-r-y peculiar.

I still don't know what caused it.

It's like my scanners. I have three 1) Canon Canoscan Lide 20. 2) Canon Canoscan 4400F and 3) Brother DCP135c Printer/scanner.
I've been searching for drivers to run these but couldn't find any. The DCP135C was I thought just an updated number of the DCP130C. No! it's a different printer and the 130 driver doesn't work.

Out of shear desperation, I plugged in the Lide 20 and started Xsane. It worked. Tried the other two and they weren't even recognised.
I found that I needed to adjust the DPI settings in Xsane to between 150-200 to get an A4 copy.

---

