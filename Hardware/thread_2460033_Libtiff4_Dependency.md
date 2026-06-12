---
title: "Libtiff4 Dependency"
date: 2021-03-31
forum: Hardware
---

### Post by cowtown-newbie on 2021-03-31
I'm very green with Ubuntu, having just installed 20.10 a week ago.

So far so good.  It was all smooth sailing, until I tried to install my Canon MX410 wireless printer.  Unfortunately, the MX410 is not in the Printer Driver database, and I ran into dead ends with other strategies I read online.

The closest I got was by following this thread:

[https://help.ubuntu.com/community/InstallCanonPixmaMx410WirelessPrinterInUbuntu](https://help.ubuntu.com/community/InstallCanonPixmaMx410WirelessPrinterInUbuntu)

I can find the driver, but when I went to install it, I received 2 dependency errors.  I was able to get past the first one, but this dependency has stumped me:

dpkg: dependency problems prevent configuration of cnijfilter-mx410series:
 cnijfilter-mx410series depends on libtiff4; however:
  Package libtiff4 is not installed.

I am able to find Libtiff4, however, when I try to install it from the command line I get this error:

dpkg: error processing archive libtiff4-dev_3.9.5-2ubuntu1.9_amd64.deb (--install):
 conflicting packages - not installing libtiff4-dev
Errors were encountered while processing:

Double clicking on libtiff4-dev and trying to install it via that route I'm warned that "these files are for the older 3.x version of the tiff libraries.  If possible, try to use the libtiff-dev package (or libtiff5-dev) package instead," and then receive the error message "The following packages have unmet dependencies."  

I do recognize that I have Libtiff5-dev installed with 20.10 rather than Libtiff4.

I really don't have much hair to pull out, but I'm at that point.  Before I give up and buy a printer that is found in the Printer Driver Database, is there someone who could point me in the right direction?



Thanks,
cowtown-newbie

---

### Post by deadflowr on 2021-04-01
Wrong libtiff4, you don't have libtiff4 you have libtiff4-dev which is not the right package.

---

