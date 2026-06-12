---
title: "How can I get SANE-AVISION scanner work in Dapper?"
date: 2006-09-07
forum: Hardware &amp; Laptops
---

### Post by olovi on 2006-09-07
I'm trying to get HP ScanJet 5370C USB scanner work in Dapper. The scanner is in supported scanners list [http://www.sane-project.org/cgi-bin/driver.pl?manu=hp&model=5370&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=hp&model=5370&bus=any&v=&p=)
 
First I tried with Xsane (0.97-4) and scanimage (sane 1.0.14-1, libsane 1.0.17-1). When I  try to preview scanner starts with promising sound, but after few seconds scanner and sane freeze. Same happens when using command scanimage. Both gives the same error message: “scanimage: sane_start: Error during device I/O”. Both 'scanimage -L' and sane-find-scanner detects ScanJet 5370C as shown below.

I tried to solve problem by editing files avision.conf  and dll.conf in /etc/sane.d/ by several different ways without results. Only thing I noticed is when I uncomment line 'option disable-calibration' in avision.conf scanner didn't even make the few seconds lasting promising sound.

Scanner worked fine in Breezy without no extra configuration, and in Dapper with VueScan. Could this problem be especially related to Dapper release? Have anyone succeeded to scan with scanner using avision backend in Dapper?

I found few threads about similar problems but they didn't help at all: [http://www.ubuntuforums.org/showthread.php?t=232231&highlight=5300c](http://www.ubuntuforums.org/showthread.php?t=232231&highlight=5300c), 
[http://www.ubuntuforums.org/showthread.php?t=191441&highlight=5370c](http://www.ubuntuforums.org/showthread.php?t=191441&highlight=5370c),
[http://www.ubuntuforums.org/showthread.php?t=221401&highlight=5300C](http://www.ubuntuforums.org/showthread.php?t=221401&highlight=5300C),
[http://www.ubuntuforums.org/showthread.php?t=191714&highlight=5300C](http://www.ubuntuforums.org/showthread.php?t=191714&highlight=5300C),
[http://www.ubuntuforums.org/showthread.php?t=7930&highlight=5300C](http://www.ubuntuforums.org/showthread.php?t=7930&highlight=5300C)

I would really appreciate any advice with this issue!



---------------
$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [Hewlett Packard], product=0x0701 [Hewlett Packard ScanJet 5300C/5370C ]) at libusb:002:028
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
---------------
$ sudo scanimage -L
device `avision:libusb:002:029' is a Hewlett-Packard ScanJet 5370C flatbed scanner
---------------

---

### Post by zxee on 2006-09-07
Have you tried to start xsane from the terminal and note/copy the output when it stops working?
I would also check the sane backend version on your system compared to what sane's website has for that scanner, and lastly consider filing a bug report through launchpad. There are things that worked in breezy that don't in dapper :(

---

### Post by olovi on 2006-09-08
> **zxee said:**
> Have you tried to start xsane from the terminal and note/copy the output when it stops working?

Yes I have tried, but there is actually no output.

My scanner is supported in latest build for sure, so I compiled latest backends (sane-backends-1.0.18.tar.gz) using a guide from Avision website [http://www.exactcode.de/oss/avision/compiling.html](http://www.exactcode.de/oss/avision/compiling.html). I added 'sudo' in front of every command.

After that 'sane-find-scanner' and 'scanimage -L' didn't find any USB or other scanners. Now I'm a bit stuck ](*,) . Any suggestions?

---

