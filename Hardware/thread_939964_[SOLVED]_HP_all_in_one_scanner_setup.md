---
title: "[SOLVED] HP all in one scanner setup"
date: 2008-10-06
forum: Hardware
---

### Post by smirnoff76 on 2008-10-06
Hey guys, 

I have just purchased a HP F4280 all in one printer / scanner. 

Amazingly enough the printer installed itself? Have to say was really impressed at that, however the scanner side is proving mysterious to me unfortunately. 

From doing quick google searches XSane Image Scanner should detect the scanner, is that right? Unfortunately that is not the case here so my question is how do i set up the scanner??

Any help / pointers would be majorly appreciated!!

Thanks in advance.

---

### Post by phidia on 2008-10-06
You might want to check the details on your device at the [sane site]("http://www.sane-project.org/cgi-bin/driver.pl").

Open a terminal and enter > sane-find-scanner what is the output?

---

### Post by smirnoff76 on 2008-10-06
okay so checked out the Sane site and ran the search and that didn't bring anything up at all so can only assume that Sane does not work "natively" with the model of scanner I have. 

Also ran the command you gave and that comes up with the following:


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [HP], product=0x2504 [Deskjet F4200 series]) at libusb:003:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


After getting this output I then ran scanimage-l from terminal and got "no sane devices found"

So where do I go from here??

---

### Post by smirnoff76 on 2008-10-06
Good news I got it up and running w00t!!

Basically I checked the version of HLIP i was running (2.8.2) and found that there was a newer version (2.8.9) that supports my scanner. 

Installed this (without un-installing the version 2.8.2) and followed HP's install instructions throughout the install process. 

Was also very easy to go through so anyone else having the same issue with little IT know how should be able to follow the installer quite easily TBH. 

HPLIP can be downloaded from [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html) and this page also contains the installer instructions.

---

