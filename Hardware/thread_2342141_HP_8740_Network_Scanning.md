---
title: "HP 8740 Network Scanning"
date: 2016-11-04
forum: Hardware
---

### Post by cmcanulty on 2016-11-04
I spent a very frustrating 10 hours yesterday trying to make our new library HP 8740 multifunction printer work over our LAN. I am running xubuntu 16.04. The print setup was easy and fast. Scanning though is a huge hassle. I already had HPLIP installed but also went through the hplip setup recommended here 

[http://hplipopensource.com/hplip-web/install/install/index.html]("http://hplipopensource.com/hplip-web/install/install/index.html")

Also their page clearly shows it is supported

HPLIP 3.16.5 - This release has the following changes:
Added Support for the Following New Printers:

- HP OfficeJet 200 Mobile Printer Series
- HP OfficeJet Pro 8710 All-in-One Printer
- HP OfficeJet Pro 8715 All-in-One Printer
- HP OfficeJet Pro 8740 All-in-One Printer
- HP OfficeJet Pro 8720 All-in-One Printer
- HP OfficeJet Pro 8725 All-in-One Printer
- HP LaserJet Pro M501n
- HP LaserJet Pro M501dn

Added support for the following new Distro's:

- Ubuntu 16.04
- Debian 8.4

Here is the issue though, the hplip install leads to dependency hell. I installed all of the dependencies I could but some don't seem to exist in any repository.

pyqt5-dbus           gui_qt5              REQUIRED            
pyqt5                gui_qt5              REQUIRED   

these in turn require more things that are not anywhere. Need to get this done on13 computers or we go back to linux is limited conversation at the library.

---

### Post by jimmy51 on 2017-01-31
> **cmcanulty said:**
> I spent a very frustrating 10 hours yesterday trying to make our new library HP 8740 multifunction printer work over our LAN. I am running xubuntu 16.04. The print setup was easy and fast. Scanning though is a huge hassle. I already had HPLIP installed but also went through the hplip setup recommended here 

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Also their page clearly shows it is supported

HPLIP 3.16.5 - This release has the following changes:
Added Support for the [[COLOR=#000000]HP OfficeJet Pro 8740 driver[/COLOR]]("https://www.printerdriverforwindows.com/hp-officejet-pro-8740-all-in-one-printer-driver-download") Following New Printers:

- HP OfficeJet 200 Mobile Printer Series
- HP OfficeJet Pro 8710 All-in-One Printer
- HP OfficeJet Pro 8715 All-in-One Printer
- HP OfficeJet Pro 8740 All-in-One Printer
- HP OfficeJet Pro 8720 All-in-One Printer
- HP OfficeJet Pro 8725 All-in-One Printer
- HP LaserJet Pro M501n
- HP LaserJet Pro M501dn

Added support for the following new Distro's:

- Ubuntu 16.04
- Debian 8.4

Here is the issue though, the hplip install leads to dependency hell. I installed all of the dependencies I could but some don't seem to exist in any repository.

pyqt5-dbus           gui_qt5              REQUIRED            
pyqt5                gui_qt5              REQUIRED   

these in turn require more things that are not anywhere. Need to get this done on13 computers or we go back to linux is limited conversation at the library.

me to having same problem xubuntu 16.10.
i think upcoming updates will fix the problem

---

