---
title: "Canon MF3010 - only scanning, Ubuntu 13.10"
date: 2013-12-17
forum: Hardware
---

### Post by ilias-utcpd on 2013-12-17
Dear all,

I bought Canon MF3010 printer/scanner. Printing is fine (thanks to the Ubuntu 13.10, 64bit, provided driver); however, the scanning does not work.

I installed the proper package, [sane-backends]("https://launchpad.net/ubuntu/+source/sane-backends"), [xsane]("http://www.xsane.org/") and simple-scan own scanning programs.However, none of them is able to detect the new Canon MF3010 scanner.

The device manufacturer is providing only Linux print support, but Canon (i[COLOR=#000000][FONT=Times New Roman]-SENSYS) MF3010 model is among [SANE supported devices]("http://www.sane-project.org/sane-mfgs.html").[/FONT][/COLOR]



Any help, please ?

[HR][/HR]
Scanner detection says:


sudo sane-find-scanner


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


found USB scanner (vendor=0x04a9 [Canon Inc], product=0x2759 [MF3010]) at libusb:001:008
found USB scanner (vendor=0x093a, product=0x2621) at libusb:001:005
found USB scanner (vendor=0x0cf3 [ATHEROS], product=0x9271 [USB2.0 WLAN]) at libusb:001:002
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
[HR][/HR]scanimage -V
scanimage (sane-backends) 1.0.25git; backend version 1.0.25


sudo scanimage -L


No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).




Post Tags: Canon MF3010, scanner, Ubuntu 13.10[HR][/HR]

---

### Post by ilias-utcpd on 2013-12-17
OK, now I installed also [FONT=verdana][COLOR=#014990][sane-backends-1.0.24.tar.gz]("https://alioth.debian.org/frs/?group_id=30186") and libusb-dev; scanned finding improved, but still, no scanner detected...

Maybe I should do something around conf-files ?
[/COLOR][/FONT]ls /etc/sane.d/
canon_dr.conf  dll.d/  fujitsu.conf  genesys.conf  geniusvp2.conf  gt68xx.conf  kodakaio.conf  saned.conf  xerox_mfp.conf


[FONT=verdana][COLOR=#014990]
[/COLOR][/FONT]sudo sane-find-scanner


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


found USB scanner (vendor=0x04a9 [Canon Inc], product=0x2759 [MF3010]) at libusb:001:009
found USB scanner (vendor=0x093a, product=0x2621) at libusb:001:005
found USB scanner (vendor=0x0cf3 [ATHEROS], product=0x9271 [USB2.0 WLAN]) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
----------------------------------------------------------------------------------------------------

Even after adding myself to the group 'scanner' and loggoff/login I am detecting "No scanners were identified."...

---

