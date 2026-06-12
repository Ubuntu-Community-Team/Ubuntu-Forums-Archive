---
title: "Success Story:  Canon ImageClass MF4000 series with network access"
date: 2013-12-25
forum: Hardware
---

### Post by George Heine on 2013-12-25
Purchased a Canon ImageCLASS MF4880dw printer in February 2013.  At the time, there was no Linux support.   A driver (260) did become available in April or May, and has gone through at least two revisions since then (currently at 2.70).   This post describes my steps to successfully install the driver.  Hope that it is useful.

PRELIMINARIES:  
Computer is a desktop (Dell Optiplex gx620) with Ubuntu 12.04 LTS.  
The printer is on our internal network, with IP 192.168.0.2.   This was configured on the printer itself.
Printer has a wireless connection, desktop has a wired connection.

DOWNLOAD DRIVER
Browse to [http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/](http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/), search for your printer, select "Drivers and Software", look for a Linux driver, and download the tar file (mine was about 75mb).   I installed in /usr/local/tar.

EXTRACT THE EXECUTABLES
```
$ cd /usr/local/tar
$ sudo tar -zxvf Linux_UFRII_PrinterDriver_V270_us_EN.tar.gz Linux_UFRII_PrinterDriver_V270_us_EN/32-bit_Driver/Debian/
# Optional but useful:
#$ sudo tar -zxvf Linux_UFRII_PrinterDriver_V270_us_EN.tar.gz Linux_UFRII_PrinterDriver_V270_us_EN/Documents/
# Optional:
#$ sudo tar -zxvf Linux_UFRII_PrinterDriver_V270_us_EN.tar.gz Linux_UFRII_PrinterDriver_V270_us_EN/Sources/
```
INSTALL LIBRARY AND DRIVER
```
$ cd /usr/local/tar/Linux_UFRII_PrinterDriver_V270_us_EN/32-bit_Driver/Debian/
$ sudo dpkg  -i cndrvcups-common_2.70-1_i386.deb
$ sudo dpkg  -i cndrvcups-ufr2-us_2.70-1_i386.deb
$ sudo /usr/sbin/lpadmin -p Canon -m CNCUPSMF4800ZS.ppd -v lpd://192.168.0.2/CanonPrinter -E

```
TEST THE INSTALLATION
```
$ lpinfo -v
...
network socket://192.168.0.2

```

There should be a message like "network socket://192.168.0.2" somewhere in the output.

---

