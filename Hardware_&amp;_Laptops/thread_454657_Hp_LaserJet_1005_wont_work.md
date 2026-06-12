---
title: "Hp LaserJet 1005 wont work?"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by elmeri on 2007-05-25
Ok, I am runing a fresh install of Ubuntu Feisty Fawn and I am unable to get my printer to work.

I have done everything I could find to solve this situation, but none helped. After I tried to install printer with ubuntu's default daemons => not working (worked in dapper september 2006). Then I formated/reinstalled my system and fiddled with other options I found from net, but those did not work either. Lastly I tried compiling the whole foo2zjs from sources and followed these instructions and everything went well, but the printer does not work :( Could you please help me to solve this issue?

What I have done so far:
$ sudo apt-get install build-essential
$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
$ tar zxf foo2zjs.tar.gz
$ cd foo2zjs
$ sudo make uninstall
$ make
$ ./getweb 1005
$ sudo make install install-hotplug cups
$ sudo gnome-cups-manager
$ sudo make cups

lsusb:
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 03f0:1317 Hewlett-Packard LaserJet 1005
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000

The printer works perfectly in Microsoft Windows XP (tested already, so no hardware malfunction...)

Printer gets its jobs, but nothing comes out from it. It seems that the driver or what ever sends the correct information somewhere but not to printer.

Here is a printerbuginfo script results:
== System information ==
Ubuntu Release : 7.04 (feisty)
Desktop Environment: GNOME
Architecture : i686
Kernel : 2.6.20-15-generic
Locale : LANG=en_US.UTF-8, LC_CTYPE=en_US.UTF-8, LC_PAPER=en_US.UTF-8
/etc/papersize : letter

== Configured printers ==
LaserJet-1005: HP LaserJet 1005 Foomatic/foo2zjs (recommended)
device for LaserJet-1005: hp:/usb/hp_LaserJet_1005_series?serial=?

== Installed versions of important printing packages ==
ii cupsys 1.2.8-0ubuntu8 Common UNIX Printing System(tm) - server
ii cupsys-driver-gutenprint 5.0.0.99.1-0ubuntu2 printer drivers for CUPS
ii foo2zjs 20061224-0ubuntu3 Support for printing to ZjStream-based print
ii foomatic-db 20070327-0ubuntu1 OpenPrinting printer support - database
ii foomatic-db-engine 3.0.2-20070303-0ubuntu1 OpenPrinting printer support - programs
ii foomatic-db-hpijs 20070327-0ubuntu1 OpenPrinting printer support - database for
ii foomatic-filters 3.0.2-20070323-0ubuntu1 OpenPrinting printer support - filters
ii gnome-cups-manager 0.31-3ubuntu5 CUPS printer admin tool for GNOME
ii gs-common 0.3.11ubuntu1 Common files for different Ghostscript relea
ii gs-esp 8.15.4.dfsg.1-0ubuntu1 The Ghostscript PostScript interpreter - ESP
ii gs-esp-x 8.15.4.dfsg.1-0ubuntu1 The Ghostscript PostScript interpreter - ESP
ii gutenprint-locales 5.0.0.99.1-0ubuntu2 locale data files for Gutenprint
ii hpijs 2.7.2+1.7.3-0ubuntu1 HP Linux Printing and Imaging - gs IJS drive
ii hpijs-ppds 2.7.2+1.7.3-0ubuntu1 HP Linux Printing and Imaging - HPIJS PPD fi
ii hplip 1.7.3-0ubuntu1 HP Linux Printing and Imaging System (HPLIP)
ii libgnomeprint2.2-0 2.18.0-0ubuntu1 The GNOME 2.2 print architecture - runtime f
ii min12xxw 0.0.9-1build1 Printer driver for KonicaMinolta PagePro 1[2
ii openprinting-ppds 20070327-0ubuntu1 OpenPrinting printer support - PostScript PP
ii pnm2ppa 1.12-16 PPM to PPA converter

Created with printingbuginfo script v1.5 ([https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript))
Sat, 26 May 2007 01:10:43 +0300

---

### Post by mitch.c on 2007-05-26
Please provide output from the following commands:
```
$ lpinfo -v
$ lpstat -t
```

---

### Post by stchman on 2008-01-15
Try my foo2zjs scrpts.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

Sounds like you don't have build-essential installed.

---

