---
title: "Microtek Slimscan c6 not working"
date: 2005-01-19
forum: Hardware &amp; Laptops
---

### Post by jsusanka on 2005-01-19
any help is greatly appreciated - I have a microtek slimscan c6 which is fully supported  by sane according to their homepage and it also worked under fedora core2 and suse 9.1 but I can't get it to work under Ubuntu - which I personally think is better than the two listed above but I have just this small problem. 

here is my info below - it shows up in the message file and the usb subsystem sees it but xsane does not detect it.  scanimage -L does not show it either - and I have changed permissions in /proc/usb/bus/xxx/xxx and ran as root but I still get the same result as below:  here is the info 


Jan 18 22:57:32 localhost kernel: SCSI subsystem initialized
Jan 18 22:57:32 localhost kernel: microtek usb (rev 0.4.3): model Phantom C6 is not known to be fully supported, reports welcome!
Jan 18 22:57:32 localhost kernel: scsi0 : microtekX6
Jan 18 22:57:32 localhost kernel:   Vendor:           Model: Scanner 600A4     Rev: 1.23
Jan 18 22:57:32 localhost kernel:   Type:   Scanner                            ANSI SCSI revision: 02
Jan 18 22:57:32 localhost kernel: usbcore: registered new driver microtekX6

> lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:1904 Hewlett-Packard DeskJet 3820
Bus 001 Device 003: ID 05da:009a Microtek International, Inc. Phantom C6
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 0000:0000  

> sane-find-scanner

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x05da, product=0x009a) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

> scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

any help would be greatly appreciated because ubuntu is probably the distro I will stay with just because of apt-get and their hardware detection is superb - (except for this).

---

### Post by jsusanka on 2005-01-19
okay,

I read the manual for sane and it appears this scanner needs the sg module which wasn't loaded - when I modprobe sg and did a scanimage -L it shows up now

I know - RTFM - sorry for taking anyone's time 

and UBUNTU ROCKS!! :D

---

