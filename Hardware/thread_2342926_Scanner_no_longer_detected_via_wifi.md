---
title: "Scanner no longer detected via wifi"
date: 2016-11-11
forum: Hardware
---

### Post by fangorn2 on 2016-11-11
I downloaded early this year the printer and scanner drivers for my Epson stylus SX235W from the [Epson download page]("http://download.ebz.epson.net/dsc/search/01/search/searchModule").

me@SATELLITE-L50-A-161:~ $ dpkg -l | grep iscan
ii  iscan                                                 2.30.3-1                                            amd64        simple, easy to use scanner utility for EPSON scanners
ii  iscan-data                                          1.38.0-1                                            all              Image Scan! for Linux data files
ii  iscan-network-nt                                 1.1.1-1                                              amd64  

The device has a dedicated static ip in my router: 192.168.0.102
Once installed my all-in-one device was working fine via wifi until recently:  the printer still works as before but the scanner is no longer  recognised.
Now simple scan reports:
Failed to scan
No scanners available. Please connect a scanner

me@SATELLITE-L50-A-161:~ $ scanimage -L
No scanners were identified.

I tried to edit etc/sane.d/epkowa.conf adding 'net autodiscovery' or 'net 192.168.0.102' but nothing changed.
I recently enabled ufw with the default set of rules and made no other changes.
My system is regurarly updated.
The scanner works via usb.

---

