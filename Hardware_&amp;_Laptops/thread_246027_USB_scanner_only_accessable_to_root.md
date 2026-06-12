---
title: "USB scanner only accessable to root"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by FishB8 on 2006-08-28
Does anybody know how to allow normal users to access a USB scanner without having to run the scanner apps using sudo?

There is no device node created for the scanner device, I have SANE set to accesses it directly from libusb using the vendor and product IDs. Is there a way to allow normal users to access it this way? Is this type of access restricted to a particular group? Will I have to make a UDEV rule to create a dev node, assigned to the "scanner" group in order for normal users to access it properly?

Thanks.

---

### Post by Shattered_Mind on 2006-08-29
I have an Epson Stylus CX4800 the way I got mine working was to do the following:

1) run sudo sane-find-scanner
Output:
found USB scanner (vendor=0x04b8 [EPSON], product=0x0819 [USB2.0 MFP(Hi-Speed)]) at libusb:003:009

2) sudo gedit /etc/udev/rules.d/45-libsane.rules
Add lines:
# Epson Corp.|Stylus CX4800
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0819", MODE="664", GROUP="scanner"

3) unpluged my scanner
4) pluged it in again and ran xsane

Note:
Because I hade run xsane as root it gave me some file save errors. To fix this I just ran > sudo chown -R <your user name> ~/.sane

Hope this helps

---

### Post by FishB8 on 2006-08-30
Thanks, that will probably do it. (especially since I'm using the exact same printer/scanner combo)

---

