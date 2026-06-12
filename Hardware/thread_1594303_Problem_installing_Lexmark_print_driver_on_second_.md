---
title: "Problem installing Lexmark print driver on second computer"
date: 2010-10-12
forum: Hardware
---

### Post by williepabon on 2010-10-12
I moved a Lexmark Z2320 printer from a DELL desktop to a DELL Workstation (Xeon cpu). The printer worked perfectly on my desktop, but when I installed the driver (lexmark-inkjet-08-driver-1.0-1.i386.deb.sh) on the workstation, I get the following message:

"The installer has detected the operating system does not meet CUPS minimum version requirements. Please, install CUPS version 1.2 or higher", and the installation stops.

Both machines have same OS version 10.04 (Lucid) LTS (different kernels, though). Here is a listing of the CUPS software installed on the workstation:

williepabon@WP-WrkStation:~$ dpkg -l | grep cup
ii  bluez-cups                            4.60-0ubuntu8                                   Bluetooth printer driver for CUPS
ii  cups                                  1.4.3-1ubuntu1.2                                Common UNIX Printing System(tm) - server
ii  cups-bsd                              1.4.3-1ubuntu1.2                                Common UNIX Printing System(tm) - BSD comman
ii  cups-client                           1.4.3-1ubuntu1.2                                Common UNIX Printing System(tm) - client pro
ii  cups-common                           1.4.3-1ubuntu1.2                                Common UNIX Printing System(tm) - common fil
ii  cups-driver-gutenprint                5.2.5-0ubuntu1.1                                printer drivers for CUPS
ii  ghostscript-cups                      8.71.dfsg.1-0ubuntu5.3                          The GPL Ghostscript PostScript/PDF interpret
ii  libcups2                              1.4.3-1ubuntu1.2                                Common UNIX Printing System(tm) - Core libra
ii  libcupscgi1                           1.4.3-1ubuntu1.2                                Common UNIX Printing System(tm) - CGI librar
ii  libcupsdriver1                        1.4.3-1ubuntu1.2                                Common UNIX Printing System(tm) - Driver lib
ii  libcupsimage2                         1.4.3-1ubuntu1.2                                Common UNIX Printing System(tm) - Raster ima
ii  libcupsmime1                          1.4.3-1ubuntu1.2                                Common UNIX Printing System(tm) - MIME libra
ii  libcupsppdc1                          1.4.3-1ubuntu1.2                                Common UNIX Printing System(tm) - PPD manipu
ii  python-cups                           1.9.49-0ubuntu1                                 Python bindings for CUPS
ii  python-cupshelpers                    1.2.0+20100408-0ubuntu5.2                       Python modules for printer configuration wit

Really appreciate any help given to solve this issue :confused:. Thanks.
wp

---

### Post by williepabon on 2010-10-12
this problem was resolved by Nathan726 on:

[http://ubuntuforums.org/showthread.php?p=7713382#post7713382](http://ubuntuforums.org/showthread.php?p=7713382#post7713382)

---

