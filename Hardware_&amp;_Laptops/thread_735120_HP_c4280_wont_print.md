---
title: "HP c4280 wont print"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by williamson389 on 2008-03-25
My Printer is an Hp all in one C4280.  It is listed as being compatible with ubuntu.  When i send something to print nothing happens.  The printer does show up when looking in adminstration-printing or preferences-default printer.  It lists the printer as processing yet i see no signs of activity.  i have yet to use this printer with ubuntu as i just upgraded a couple weeks ago.

Thanks in advance

---

### Post by williamson389 on 2008-03-25
i dont know but i think i might just have to run hplip.  i ran hplip for the first time and the installer failed.  the terminal said this.  Do i have to have the ubuntu cd in?


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp-dev python-qt3 python-reportlab libsane-dev python-imaging libsane cupsddk cupsddk-drivers'
Please wait, this may take several minutes...
|error: No output seen in over 300 sec... (Is the CD-ROM/DVD source repository enabled? It shouldn't be!)
fatal error: :hplip-install
error: Package install command failed with error code 1
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo apt-get install --yes --force-yes build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp-dev python-qt3 python-reportlab libsane-dev python-imaging libsane cupsddk cupsddk-drivers'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo apt-get install --yes --force-yes build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp-dev python-qt3 python-reportlab libsane-dev python-imaging libsane cupsddk cupsddk-drivers'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? n
warning: Some HPLIP functionality might not function due to missing package(s).


RUNNING POST-PACKAGE COMMANDS
-----------------------------


RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'gcc (gcc - GNU Project C and C++ Compiler)' is still missing.
error: A required dependency 'libpthread (libpthread - POSIX threads library)' is still missing.
error: A required dependency 'python-devel (python-devel - Python development files)' is still missing.
error: A required dependency 'cups-devel (cups-devel- Common Unix Printing System development files)' is still missing.
error: A required dependency 'libusb (libusb - USB library)' is still missing.
error: A required dependency 'libtool (libtool - Library building support services)' is still missing.
error: A required dependency 'libjpeg (libjpeg - JPEG library)' is still missing.
error: Installation cannot continue without these dependencies.
error: Please manually install this dependency and re-run this installer.

---

### Post by 11hjpphty76lkjj on 2008-03-27
What's happening is that the cd is still setup as a repository source.  Please disable the cd source by going to:

System
Administration
Software Sources

Make sure there are no check marks next to the cd repos and click okay and reload and try again.

Hopefully this will correct your install problem.

All the best,

Aaron

---

