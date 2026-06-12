---
title: "trying to install canon driver"
date: 2016-08-16
forum: Hardware
---

### Post by jgw on 2016-08-16
I just upgraded to 16.04 on this machine.  Now I want to setup my canon mg5722 printer.  I have downloaded the canon drivers for an mg5722 and am trying to install same.  When I tried the install I found a LOT of missing dependencies.  I guess I could goto synaptic but there must be a better way?

Following directions I found on the net I entered (after downloading the drivers (cnijfilter2-5.2-1-x86_64.rpm)):
sudo su -c "./install.sh"  (this install was included with the driver download so I assume it knew what it was doing)

and got:
Command executed = rpm -Uvh ./packages/cnijfilter2-5.20-1.x86_64.rpm
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: Failed dependencies:
	/bin/sh is needed by cnijfilter2-5.20-1.x86_64
	cups is needed by cnijfilter2-5.20-1.x86_64
	libc.so.6()(64bit) is needed by cnijfilter2-5.20-1.x86_64
	libc.so.6(GLIBC_2.2.5)(64bit) is needed by cnijfilter2-5.20-1.x86_64
	libc.so.6(GLIBC_2.3)(64bit) is needed by cnijfilter2-5.20-1.x86_64
	libc.so.6(GLIBC_2.7)(64bit) is needed by cnijfilter2-5.20-1.x86_64
	libcups.so.2()(64bit) is needed by cnijfilter2-5.20-1.x86_64
	libcupsimage.so.2()(64bit) is needed by cnijfilter2-5.20-1.x86_64
	libdl.so.2()(64bit) is needed by cnijfilter2-5.20-1.x86_64
	libdl.so.2(GLIBC_2.2.5)(64bit) is needed by cnijfilter2-5.20-1.x86_64
	libpthread.so.0()(64bit) is needed by cnijfilter2-5.20-1.x86_64
	libusb-1.0.so.0()(64bit) is needed by cnijfilter2-5.20-1.x86_64
	libxml2.so.2()(64bit) is needed by cnijfilter2-5.20-1.x86_64
	libxml2.so.2(LIBXML2_2.4.30)(64bit) is needed by cnijfilter2-5.20-1.x86_64
	libxml2.so.2(LIBXML2_2.6.0)(64bit) is needed by cnijfilter2-5.20-1.x86_64
	rtld(GNU_HASH) is needed by cnijfilter2-5.20-1.x86_64

its a bit strange.  for instance, cups is installed yet the above says cups is needed.  

Thank you................

---

### Post by weatherman2 on 2016-08-16
Isn't there a Debian version?  There usually is on the Canon site.  Don't start with the RPM version.

---

### Post by jgw on 2016-08-16
Thanks for the reply!

This is the file that comes from the canon site.  its also the one that virtually everybody recommends.  I am quite willing to try another but this is the one on the canon site (asia)  Here is a link to one of the sites that recommend: [http://tutorialforlinux.com/2015/11/05/how-to-install-canon-mg5722-printer-driver-on-ubuntu-15-10-wily-32-64bit-quickstart-scanning-easy-guide/](http://tutorialforlinux.com/2015/11/05/how-to-install-canon-mg5722-printer-driver-on-ubuntu-15-10-wily-32-64bit-quickstart-scanning-easy-guide/)   The recommended driver is:  IJ Printer Driver Ver. 5.20 for Linux (rpm Packagearchive)

---

### Post by weatherman2 on 2016-08-16
I found the Debian version on the Europe site.  I searched for MG5750 (because 5722 must not be sold in Europe), but it is IJ Printer Driver version 5.20 - ought to work:

[http://www.canon-europe.com/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg5750.aspx?type=drivers&driverdetailid=tcm:13-1299548&os=LINUX&language=EN](http://www.canon-europe.com/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg5750.aspx?type=drivers&driverdetailid=tcm:13-1299548&os=LINUX&language=EN)[FONT=arial]

[/FONT]

---

### Post by jgw on 2016-08-17
Thank you for the replies!

That is, exactly, what I have!  I think the problem is that, when I upgraded to 16.04, that these were not installed.  I am going to use synaptic to get the missing stuff.

I then went to the Europe site and downloaded that driver.  I then compared the driver from asia and the one from europe and the european one was much larger than the one from asia.  So, I installed the driver with gdebi and then installed the printer from system settings.  The printer now seems to be working.  My next task is to figure out if the printer is using the driver I think I installed <G>

I also found it interesting that the asian canon site's driver and the european driver were not the same file even though they had the same name.  

Thanks again!

---

