---
title: "hp officejet 5510 works under dapper , but not under edgy"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by Nasir Amra on 2007-01-14
Well after 2 days trying to figure out how to upgrade from dapper to edgy, I finally did a new install for edgy. However, one big problem I have is that the officejet 5510 ( using the officejet 5500 driver ) only prints empty pages when I click on test page button (both as regular officejet driver connection and a RAW connection).  I've listed what I have installed related to cups below at the end of my message. I've spent all day googling and trying various maneuvers ( install and uninstall cups) , but with no success. It's puzzling that it used to work right away with dapper , but not with edgy. Any one have any more ideas as to what I can do to troubleshoot this problem?



root@amd:/etc# dpkg -l | grep cups
ii  cups-pdf                                   2.4.2-1                              PDF printer for CUPS
ii  cupsys                                     1.2.4-2ubuntu3                       Common UNIX Printing System(tm) - server
ii  cupsys-bsd                                 1.2.4-2ubuntu3                       Common UNIX Printing System(tm) - BSD comman
ii  cupsys-client                              1.2.4-2ubuntu3                       Common UNIX Printing System(tm) - client pro
ii  cupsys-common                              1.2.4-2ubuntu3                       Common UNIX Printing System(tm) - common fil
ii  cupsys-driver-gutenprint                   5.0.0-2ubuntu2                       printer drivers for CUPS
ii  gnome-cups-manager                         0.31-1.1ubuntu14                     CUPS printer admin tool for GNOME
ii  libcupsimage2                              1.2.4-2ubuntu3                       Common UNIX Printing System(tm) - image libs
ii  libcupsys2                                 1.2.4-2ubuntu3                       Common UNIX Printing System(tm) - libs
ii  libgnomecups1.0-1                          0.2.2-5ubuntu1                       GNOME library for CUPS interaction
ii  libgnomecupsui1.0-1c2a                     0.31-1.1ubuntu14                     UI extensions to libgnomecups

---

### Post by marcele on 2007-01-23
I also have this problem. Anyone ?

---

