---
title: "HP F380 scanner not found after feisty beta upgrage"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by theonlykman on 2007-04-09
Hi,
So I have a HP F380 All-in-one that worked fine (printer, scanner, the whole deal) with Edgy 6.10. However, I had unreliable networking with 6.10 so I upgraded to Feisty a little while ago and so far it has been a dream. 
But, as far as I can tell, once I upgraded, I lost the use of the scanner (the printer still works fine and the scanner still works in Windows). Im not sure if its because of the upgrade so this could be a post hoc fallacy on my part.

Xsane keeps on giving me the "no device found" dialog.

Also, the hpaio backend wasnt listed at all in the dll.conf file (though it was listed in a seperate file).

Ive gone through numerous forums to no avail (either I've havent found the correct diagnosis, or I'm going about fixing it the wrong way). Im beginning to think its a faulty hardware issue but it does still work in Windows so I dont know.
Perhaps the version of HPLIP that I have (1.7.3) is too new and lost support for the printer?
I would really appreciate a step by step procedure for diagnosing and fixing my problem.
 
Thanks a bunch!

After running hp-check I get:
> HP Linux Imaging and Printing System (ver. 1.7.3)
Dependency/Version Check Utility ver. 5.3

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux khalid-laptop 2.6.20-14-generic #2 SMP Mon Apr 2 20:37:49 UTC 2007 i686 GNU/Linux

Detected distro (/etc/issue):
ubuntu 7.04

Detected distro (lsb_release):
Ubuntu 7.04 (feisty)

Currently installed HPLIP version...
HPLIP 1.7.3 currently installed in '/usr/lib/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf

[hpiod]
# port=0 (dynamic IP port)
port=2208
[hpssd]
# port=0 (dynamic IP port)
port=2207

[hplip]
version=1.7.3
jdprobe=0

[dirs]
home=/usr/lib/hplip
run=/var/run/hplip
ppd=/usr/share/ppd
doc=/usr/share/doc/hplip-doc/HTML

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=1
pp-build=1
gui-build=1
scanner-build=1
fax-build=1
cups11-build=0


HPLIP running?
No, HPLIP is not running (OK).

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.1 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
OK, Version 4.5 installed

----------------
| DEPENDENCIES |
----------------

 
Checking for dependency libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency SANE - Scanning library...
OK, found.

Checking for dependency GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency libjpeg - JPEG library...
OK, found.

Checking for dependency libpthread - POSIX threads library...
OK, found.

Checking for dependency make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency python-devel - Python development files...
OK, found.

Checking for dependency Reportlab - PDF library for Python...
OK, found.

Checking for dependency PyQt - Qt interface for Python...
OK, found.

Checking for dependency cups-devel- Common Unix Printing System development files...
OK, found.

Checking for dependency ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency libusb - USB library...
OK, found.

Checking for dependency scanimage - Shell scanning program...
OK, found.

Checking for dependency libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency LSB - Linux Standard Base support...
OK, found.

Checking for dependency xsane - Graphical scanner frontend for SANE...
OK, found.

Checking for dependency cups - Common Unix Printing System...
OK, found.

Checking for dependency Python 2.3 or greater - Required for fax functionality...
OK, found.


----------------------
| INSTALLED PRINTERS |
----------------------

 
DeskJet-F300
------------
Device URI: usb://HP/Deskjet%20F300%20series?serial=CN65CF80SJ04KH
Installed in HPLIP? No
PPD: /etc/cups/ppd/DeskJet-F300.ppd
PPD Description: HP DeskJet F300 Foomatic/hpijs (recommended)
Printer status: printer DeskJet-F300 is idle.  enabled since Wed 04 Apr 2007 08:14:33 PM PDT

error: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP. (You can still print to this printer using another backend and HPIJS.)


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.


1 errors were detected.
Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)



> error: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP. (You can still print to this printer using another backend and HPIJS.)

I dont understand this because as I mentioned before the scanner use to work. How do I make the scanner installed then?

> khalid@khalid-laptop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [HP], product=0x5511 [Deskjet F300 series]) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
khalid@khalid-laptop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).



and, finally:
> khalid@khalid-laptop:~$ sudo hp-setup
Password:

HP Linux Imaging and Printing System (ver. 1.7.3)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Unable to connect to hpiod.
error: Unable to connect to HPLIP I/O. Please (re)start HPLIP and try again.
khalid@khalid-laptop:~$ sudo /etc/init.d/hplip restart
 * Stopping HP Linux Printing and Imaging System                         [ OK ] 
 * Starting HP Linux Printing and Imaging System                         [ OK ] 
khalid@khalid-laptop:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 1.7.3)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Unable to connect to hpiod.
error: Unable to connect to HPLIP I/O. Please (re)start HPLIP and try agai

---

### Post by epictete on 2007-04-17
Hi **Theonlykman**, I have the same problem with a scanner Canon Lide 30 that worked perfectly under Breezy, Dapper and Edgy !

Under Feisty I get a black visualisation window.

I think that it's this **bug** (on **Launchpad**):

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

and here (french):

[http://forum.ubuntu-fr.org/viewtopic.php?pid=844939](http://forum.ubuntu-fr.org/viewtopic.php?pid=844939)

I do hope that it'll be fixed before the final release: it would be such a regression if a hardware well recognized before couldn't work anymore !

---

### Post by theonlykman on 2007-04-17
Thanks for the reply!
But I just reformatted due to other problems and did a fresh install of feisty (as opposed to an upgrade) and everything works wonderfully, again thanks

---

### Post by hardyn on 2007-04-17
I have often found that they do not detect corectly unless the power is cycled on the scanner just before detection.

---

### Post by epictete on 2007-04-17
_That's very interesting_ **Theonlykman** !

What did you use for the fresh install : the beta version or a daily build ?

And what is your kernel version &#8209; for, as many others, I can't boot with the 2.6.20-15 version:

[http://ubuntuforums.org/showthread.php?t=408053](http://ubuntuforums.org/showthread.php?t=408053)

It would be nice to give us the infos !

For scanning it is always possible to create a little script with:

```
# scannimage
#!/bin/sh
scanimage --format jpeg --resolution 300 -x 215 -y 297 > ~/Desktop/scanned_image
```

as it is said here:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=844939](http://forum.ubuntu-fr.org/viewtopic.php?pid=844939)

**hardyn**: thank's but my scanner haven't got an on/off button: it's always « on ».

---

### Post by theonlykman on 2007-04-19
hi  epictete, 
I reinstalled using the beta (kernel version 2.6.20-12 I believe?) and that pretty much fixed all the troubles that I had with the scanner. After subsequent updates kernels (20-14 and 15) my system still works fine.

I suspect that my earlier problems occured after the distro-upgrage from edgy to feisty using the update-manager.

---

### Post by epictete on 2007-04-23
- Thank you **Theonlykman**. We don't have the same problem for I'm running the 2.6.20-15-27 kernel and xsane doesn't work anymore.

- Some solutions have been given on Lauchpad till the bug is fixed.

- I'm happy your own problem is forgotten.

---

### Post by fearpi on 2007-04-27
I also have an F380 that is not being recognized as a scanner. I used the update manager to upgrade to Feisty (I am on kernel 2.16.20-15), but I'm not sure if it ever worked. Suggestions?

---

