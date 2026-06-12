---
title: "Ubuntu 10.04 and Epson Stylus Photo RX580 All-in-One Printer"
date: 2011-01-20
forum: Hardware
---

### Post by Brad55 on 2011-01-20
I just installed Ubuntu 10.04 and had no problem but the scanner that is in the printer. I have tried every thing I know to get the software to see it (unplug printer, uninstall cups and reinstall cups) but nothing seems to work. Side note I had openSUSE 11.2 on the computer and it saw both the printer and scanner. Is there a trick or two up some ones sleeve that they could pass along my way.

Please.

---

### Post by Brad55 on 2011-01-21
I found the answer to my problem.

The Epson.conf and Epson2.conf have to be edited with the correct information of the scanner.

Open up a treminal and type sudo sane-find-scanner (Note: you have to have sane installed.)

You should see some thing like this.

$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0827 [USB2.0 MFP(Hi-Speed)]) at libusb:001:007
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

Notice the (vendor=0x04b8 and product=0x0827 from the scan.

Now open up a terminal and type sudo gedit /etc/sane.d/epson.conf 

Look at the bottom of the file and you will see these lines.
Uncomment the line # usb 0x4b8 0x0827 make sure you put your correct numbers in.

# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x0827
# And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0

It did not see the scanner on the first file but xsane found it on the second file epson2.conf.

Now open up a terminal and type sudo gedit /etc/sane.d/epson2.conf

This is the line you need you need to uncomment and put your correct numbers in.

# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x0827

Uncomment the line # usb 0x4b8 0x0827 and use your numbers.

Xsane found the scanner this time and the scanner works great.

I don't know how to mark this as SOLVED so if some one could tell me ill do it.

This might work on other all-in-one printer where Ubuntu does not see the scanner.

---

