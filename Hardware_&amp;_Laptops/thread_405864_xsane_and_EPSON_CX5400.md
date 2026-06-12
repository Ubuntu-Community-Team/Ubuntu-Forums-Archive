---
title: "xsane and EPSON CX5400"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by Giana on 2007-04-10
Dear all,
On my Edgy I recently installed my old printer EPSON Stylus CX5400.
As printer it works fine, as scanne not at all.

Synthoms:
the system sees of course the device:

```

$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04b8:0808 Seiko Epson Corp. 
Bus 001 Device 001: ID 0000:0000  

```

everybody can write:

```

$ ll /dev/bus/usb/001/003
0 crw-rw-rw- 1 root scanner 189, 2 2007-04-10 12:21 003

```

sane probably sees it (but why at 001:004?)

```

$ sane-find-scanner
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0808 [USB MFP]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```

but both xsane and scanimage -L fail
```

$ scanimage -L 

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

Any help would be really appreciated. Thanks in advance,

G.

---

### Post by Giana on 2007-04-10
I've forgot: 
in kern.log, messages and syslog whnever I launch xsane the following message appears:

```
usb 1-4: usbfs: interface 1 claimed by usblp while 'xsane' sets config #1
usb 1-4: usbfs: interface 1 claimed by usblp while 'scanimage' sets config #1

```
G.

---

### Post by Giana on 2007-04-11
Nobody has suggestions?
Hints to further debug the problem?
thanks in advance,

G.

---

### Post by HellHoundsofwar on 2007-09-23
try this

copy and paste into terminal

sudo sane-find-scanner | grep 0x04b8
found USB scanner (vendor=04b8,
product=0x0808) at libusb:001:002

---

### Post by geraldm on 2007-09-23
xsane and sane-backends are setup to use only scanners that are known to work, 
and "04b8:0808" is not such a scanner, which is why that configuration does not 
appear in any file within /usr/etc/sane.d/*.conf
All sorts of problems can arise when the scanner driver is untested against a scanner.

Scanner drivers normally are created by a developer who has taken an interest in that
scanner, and does the development that adapts a driver to the features of the scanner,
and is willing to maintain that code.
You may want to post your interest to the sane-devel list at [www.sane-project.org](www.sane-project.org)
to show your interest.  Some developer needs to take the initiative to get the task underway.

Gerald

---

