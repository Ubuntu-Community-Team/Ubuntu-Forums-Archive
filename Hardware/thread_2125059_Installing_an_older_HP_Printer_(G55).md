---
title: "Installing an older HP Printer (G55)"
date: 2013-03-12
forum: Hardware
---

### Post by threedogs on 2013-03-12
I finally got my old HP G55 printer working. The following thread outlines the problem and how to solve it.

[https://answers.launchpad.net/hplip/+question/209551](https://answers.launchpad.net/hplip/+question/209551)

> If you are using HPLIP-3.12.6 or 3.12.9 version and printer G55, this may not work properly.
Somehow G55 is not supporting libusb-1.0 version and where as hplip-3.12.6 or 3.12.9 started using latest libusb-1.0 by defualt package instead libusb-0.1.

To use this G55 printer, configuration needs to be changed. Steps provided in site:-http://hplipopensource.com/hplip-web/install/manual/index.html

in configuration, use "--enable-libusb01_build" instead of "--disable-libusb01_build"

e.g. in ubuntu
change From
./configure --with-hpppddir=/usr/share/ppd/HP --prefix=/usr --enable-qt4 --**disable**-libusb01_build --enable-doc-build --enable-cups-ppd-install --disable-foomatic-drv-install --disable-foomatic-ppd-install --disable-hpijs-install --disable-udev_sysfs_rules --disable-policykit --disable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build

To:-
./configure --with-hpppddir=/usr/share/ppd/HP --prefix=/usr --enable-qt4 --**enable**-libusb01_build --enable-doc-build --enable-cups-ppd-install --disable-foomatic-drv-install --disable-foomatic-ppd-install --disable-hpijs-install --disable-udev_sysfs_rules --disable-policykit --disable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build.


Regards,
Amarnath

In the preceding quote, we are directed to an HP site

[http://hplipopensource.com/hplip-web/install/manual/index.html](http://hplipopensource.com/hplip-web/install/manual/index.html)

This link explains how to compile the HPLIP package. Unfortunately following the instructions on that page landed me in dependency hell and unable to create a make file. I found the solution here.

[http://www.liberiangeek.net/2012/12/how-to-install-hp-printer-drivers-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/12/how-to-install-hp-printer-drivers-in-ubuntu-12-10-quantal-quetzal/)

This link shows how to download and run a script that automatically resolves dependencies and installs the HPLIP package. The only problem is that installed package still disables libusb01_build (and we need it enabled). So back to the HP site and follow the instructions to recompile. The dependency issues will vanish, having been solved by the script. 

The only gotcha in all of this is that the hplip version is now different (hplip-3.13.3 at present). I just edited to the correct version when I cut/pasted the code into the terminal.

Hope this helps

---

