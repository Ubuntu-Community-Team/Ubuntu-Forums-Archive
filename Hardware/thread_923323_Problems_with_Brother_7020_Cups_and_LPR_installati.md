---
title: "Problems with Brother 7020 Cups and LPR installation."
date: 2008-09-18
forum: Hardware
---

### Post by Beandogg on 2008-09-18
Hi, I'm using Ubuntu 8.04 LTS and I've been having difficulty installing my Brother DCP-7020 printer. The problem is 2 fold:

1. the CUPS and LPRS package I downloaded from the Brother site does not install correctly.  I get this message:

Setting up cupswrapperdcp7020 (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperDCP7020-2.0.1: 64: cannot create /usr/share/cups/model/DCP7020.ppd: Directory nonexistent
 * Restarting Common Unix Printing System: cupsd
   ...done.
cp: cannot stat `/usr/share/cups/model/DCP7020.ppd': No such file or directory
dpkg: error processing cupswrapperdcp7020 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gcursor (0.061-ubuntu5) ...
Errors were encountered while processing:
 cupswrapperdcp7020
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up cupswrapperdcp7020 (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperDCP7020-2.0.1: 64: cannot create /usr/share/cups/model/DCP7020.ppd: Directory nonexistent
 * Restarting Common Unix Printing System: cupsd
   ...done.
cp: cannot stat `/usr/share/cups/model/DCP7020.ppd': No such file or directory
dpkg: error processing cupswrapperdcp7020 (--configure):
 subprocess post-installation script returned error exit status 1

2. Now everytime I sudo apt-get install anything, the packages install, but at the end of it I get this message, for instance, when installing gcursor:

Selecting previously deselected package gcursor.
(Reading database ... 154966 files and directories currently installed.)
Unpacking gcursor (from .../gcursor_0.061-ubuntu5_i386.deb) ...
Setting up cupswrapperdcp7020 (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperDCP7020-2.0.1: 64: cannot create /usr/share/cups/model/DCP7020.ppd: Directory nonexistent
 * Restarting Common Unix Printing System: cupsd
   ...done.
cp: cannot stat `/usr/share/cups/model/DCP7020.ppd': No such file or directory
dpkg: error processing cupswrapperdcp7020 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gcursor (0.061-ubuntu5) ...
Errors were encountered while processing:
 cupswrapperdcp7020
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up cupswrapperdcp7020 (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperDCP7020-2.0.1: 64: cannot create /usr/share/cups/model/DCP7020.ppd: Directory nonexistent
 * Restarting Common Unix Printing System: cupsd
   ...done.
cp: cannot stat `/usr/share/cups/model/DCP7020.ppd': No such file or directory
dpkg: error processing cupswrapperdcp7020 (--configure):
 subprocess post-installation script returned error exit status 1

I'm pretty new to Ubuntu...but I love it so far...using it for about three months, and this has been my only snag. Any help would be appreciated.  Thank you:)

---

### Post by phidia on 2008-09-18
You haven't shown the commands the README or INSTALL file gives you to execute.
But from the output it looks like you may need to use "sudo" with the command(s) you are issuing.
I can't tell anymore-if you want to post the installation steps you're following that may help.

Added: At the open printing site they list a driver for [your printer]("http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-7020") plus there are links to guides for setting it up at that page too.

---

### Post by cjazz on 2008-09-18
Have you tried creating the directory:

```
sudo mkdir /usr/share/cups/model
```

and then installing the driver?

---

### Post by Beandogg on 2008-09-21
that worked, thanks so much!

---

