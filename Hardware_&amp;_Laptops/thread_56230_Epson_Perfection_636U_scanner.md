---
title: "Epson Perfection 636U scanner"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by tiglionabbit on 2005-08-11
I plug in my scanner via USB.  lsusb lists:
Bus 003 Device 004: ID 04b8:0101 Seiko Epson Corp. Perfection 636

I start xsane.  It detects the scanner and opens four windows.  I click on "Aquire Preview" or "Scan".  It waits 60 seconds or so in hang and then shows a message box that looks like this:

--------------------------------------------Error-----------------------------------
|   (X)   Failed to start scanner. Error during device I/O  |
|   [                                  Close                                  ]   |
---------------------------------------------------------------------------------------

Running sane-find-scanner says this among things:
found USB scanner (vendor=0x04b8 [EPSON], product=0x0101 [Perfection636]) at libusb:003:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

running scanimage -L says:
device `epson:libusb:003:004' is a Epson Perfection636 flatbed scanner

running scanimage > test says:
scanimage: sane_start: Error during device I/O

I can't find the CD that came with this scanner, and there don't appear to be linux drivers on the internet.  What should I do to set it up properly?

---

