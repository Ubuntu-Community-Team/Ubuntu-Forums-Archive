---
title: "epson v600 photo installation problem"
date: 2013-09-28
forum: Hardware
---

### Post by mrkaplan on 2013-09-28
i have a hp pavillion p6-2497 with ubuntu 13.04 newly installed ; 
i encounter my first major problem with installation of my epson v600 photo scanner 
both simple scan and xsane scan image fail to start it .
sane-find-scanner tool actually sees the scanner :  report says : 

"mhb@m-p6-2497ef:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x013a [EPSON Scanner]) at libusb:001:030
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program."

then i ran scanimage-L as advised, report said :
 
"mhb@m-p6-2497ef:~$ sudo scanimage -L
[sudo] password for mhb: 

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages)."

any ideas welcome

---

### Post by Bucky Ball on 2013-09-28
*Thread moved to **Hardware**.*

***Installation & Upgrades*** for installation and upgrade of OS. ;)

---

### Post by mrkaplan on 2013-10-03
could not find what the issue was with my 13.04 system. Possibly something i did . to be safe i switched to ubuntu 12.04 . which seems reliable . then i was able to install scan drivers successfully .  Did as in this thread : 
[http://doc.ubuntu-fr.org/scanner_epson](http://doc.ubuntu-fr.org/scanner_epson)
which tells you to install 3 files : 
iscan.xxx-ltdl7
iscan data
iscan plugin   ( to be installed last )
careful choose 64 or 32 bit system . dont forget to reboot .

---

