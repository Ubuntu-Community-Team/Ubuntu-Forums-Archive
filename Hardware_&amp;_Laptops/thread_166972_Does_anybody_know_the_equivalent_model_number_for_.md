---
title: "Does anybody know the equivalent model number for the Epson ME100?"
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by new2linux9 on 2006-04-27
I bought the Epson ME100, a 3-in-1 inkjet printer in China, the only problem is that it is only known in China and I want to install it onto my Ubuntu system.  The disc it came with, suprise, suprise, is only for Windows and I do not know what the equivalent model number is.  I have asked Epson UK who couldn't help and suggested I look at the Chinese website but I can't read Chinese!  Does anybody know?  I have also already googled, sent off emails to various printer sites, epson America, basically have done everything I can think of, but still cannot find what the equivalent model number is!

Thank you for any help.

---

### Post by new2linux9 on 2006-04-29
An update.  I have installed it as a CX1500.

This is what I got when I typed lsusb in the terminal:

marco@laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 04b8:080c Seiko Epson Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 001 Device 001: ID 0000:0000
marco@laptop:~$

So now I am trying to find out what model number 080c refers to, as someone on [www.linuxprinting.org](www.linuxprinting.org) told me that: 
> 
04b8 is the code for Seiko Epson Corp. And 080c is the code for a
particular one of their products. Doesn't matter what manufacturer or
product name is silk-screened on the outside, and it's nothing to do
with Linux.

Sadly, I don't know which other better-known product name might have
that same ID. Perhaps somebody else on the list knows?

There's an index at [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids) but it's a bit out
of date. Does anybody know of a better one? I'm surprised linuxprinting
doesn't have such an index.

And this is what I got when I typed sudo sane-find-scanner:

marco@laptop:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04b8 [EPSON], product=0x080c [USB MFP]) at
libusb:002:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

Now that I have set it up as a Stylus CX1500, it partially works, only printing, but not scanning.  However I set it up as the CX1500 as this is the printer it resembles the most, both in looks and in specs, but it is just an eduacted guess.  I would be happy if somone could confirm if this is or isn't the case so that I can get on and try to get the scanner part working.

Thank you

---

