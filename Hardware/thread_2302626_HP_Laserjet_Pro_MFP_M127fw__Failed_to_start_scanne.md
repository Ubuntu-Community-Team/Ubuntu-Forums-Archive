---
title: "HP Laserjet Pro MFP M127fw  Failed to start scanner: Error during device I/O"
date: 2015-11-11
forum: Hardware
---

### Post by datamason on 2015-11-11
Hello All,
Am using Linux Mint 17.2 64-bit and have the above HP all-in-one printer installed as a network printer. Printing works fine. When I use Xsane to scan, I get the above error message (Failed to start scanner: Error during device I/O). If I click ok to close the warning box, I see that Xsane scanned fine and my image shows in the Xsane interface. For a single page, this is no problem, but when I run multiple pages through the document feeder, this is a problem. 

I have searched the internet for these keywords but no luck, except for [this link]("http://www.linux.org/threads/resolved-scanner-problem-epson-workforce-645-linux-mint-16-network.6066/") which is of now help: wrong printer, and I do not receive the error listed in posting #4. 

Using HP LIP 3.15.6 (more recent versions failed when I tried months ago). Sane version 1.0.23
Terminal command hp-scan (one page only utility) scanned w/o error, although
Tried editing hp.conf to uncomment the line: option dumb-read even though my connection is a network connection. No change to the problem.
Of course, the HP Device Manager calls Xsane to scan, so that achieves nothing. 

Any ideas?

---

### Post by tgalati4 on 2015-11-12
How old it the printer?  Sometimes the scan light is not bright enough (because of old age) causing the printer-scan-ready to time out.  One way to test is to plug the printer in the hottest outlet.  If you have 118VAC vs 124VAC, use the 124VAC plug.  That few extra volts will make the bulb brighter and cause the scanner to remain ready longer.  If on a power strip, remove and plug into the wall directly.

If the glass is dirty, try cleaning.  A failing power brick will also cause scan problems.

If you get any scan timeout errors at the printer's front panel, then you know the bulb is worn out or the inverter is failing or the power brick is failing.

I did have an Officejet printer act strange when the gigabit router it was hooked to started flashing.  The 12VDC wall wart was failing.  So check your router or plug into USB and test with USB to isolate the issue.

---

### Post by datamason on 2015-11-12
Thanks tgalati4,
The HP is around 12 months old. I tried plugging it directly into the wall socket. I should point out that the scanner works fine just using the Simple Scan app. For that matter, scanning is working also with Xsane, only I get the spurious I/O error which stops multipage doc feeder scans. All in all, scanning works w/o problem, including also on my Win 10 machine. So I am not seeing this as a hardware problem.

I do not understand how to configure Sane, nor how it interacts with Xsane. It is not clear to me if Simple Scan is using the Sane backend. I would like to continue to use Xsane because of the options it offers. 
Michael

---

### Post by tgalati4 on 2015-11-12
There is only one scanning framework:  SANE, everything else hooks into it or is a front-end to it.  Even *hp-scan* uses SANE.  

Try a USB cable to isolate a network I/O error versus a SANE error.  Try a multi-scan to an SD card on the printer directly and see if the image file is complete.  Check your log files in /var/log and /var/log/cups to see if there are any I/O errors.

---

