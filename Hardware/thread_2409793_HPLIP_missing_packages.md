---
title: "HPLIP missing packages"
date: 2019-01-06
forum: Hardware
---

### Post by goodstuff9 on 2019-01-06
Ubuntu 18.04.1, HPLIP 3.17.10.  

I am attempting to install HPLIP using Synaptic.  The installation reports no errors.  But, when I start the HP system tray, I get this error message:  


File "/usr/bin/hp-toolbox", line 269, in <module>
     QApplication, ui_package = utils.import_dialog(ui_toolkit)
 TypeError: 'NoneType' object is not iterable

Also, the HP icon in the tray area does nothing if I click on it - although I am able to start the HPLIP Toolbox, and that seems to work.  

When I run hp-check, it tells me that these packages are missing/incompatible, and that I need to install them manually:  

libnetsnmp-devel
snmp-mibs-downloader
libsnmp-dev

I do not know where to find the first two, nor how to install them manually.  

Regarding libsnmp-dev:  It is not installed, but via Synaptic versions 5.7.3+dfsg-1.8ubuntu3 and 5.7.3+dfsg-1.8ubuntu3.1 are available to install.  However, when I try to install libsnmp-dev via Synaptic, it tells me that the following packages will be removed - but I don't want them to be removed (especially npm):  

libssl1.0-dev
node-gyp
nodejs-dev
npm

So, I need some help here:  How do I get the missing packages installed, get HPLIP working, get rid of the error message (above), and make the HP system tray to work, without uninstalling npm and those other packages?

---

### Post by mikasu on 2019-01-07
I am not sure but I think the packages you want interferes with the ones hplip needs... It's for a HP Printer?

---

