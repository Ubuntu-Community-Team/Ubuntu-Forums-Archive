---
title: "ZV5000 Bluetooth"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by skydiver|goose on 2008-03-01
How can I get it working?

I'm on an HP Pavilion ZV5000, running the most up-to-date version of Ubuntu. I followed the Ubuntu documentation to try and get it running, but here's what Terminal displays:

goose@goose-laptop:~$ sudo apt-get install bluez-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bluez-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
goose@goose-laptop:~$ sudo /etc/init.d/bluetooth restart
 * Restarting Bluetooth services                                         [ OK ] 
goose@goose-laptop:~$ hcitool dev
Devices:
goose@goose-laptop:~$

---

