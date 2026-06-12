---
title: "Epson scanner install problem: access denied"
date: 2011-07-03
forum: Hardware
---

### Post by dargaud on 2011-07-03
Hello all,
I just did a fresh install of KUbuntu 11.04 and I have trouble reinstalling the "Epson Perfection V500 Photo" scanner which used to work fine in 10.10.
I'm following the instructions found in the pdf at the botto, of [this pqge]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do"). On page 9 it talks about changing permission, but I have no /proc/bus/usb/001/002. So here's what I did:
```
$ sudo dpkg --install iscan-data_1.9.0-1_all.deb
$ sudo dpkg --install iscan_2.26.4-2.ltdl7_amd64.deb
$ sudo dpkg --install iscan-plugin-gt-x770_2.1.2-1_amd64.deb
$ sane-find-scanner | grep 0x04
found USB scanner (vendor=0x04b8, product=0x0130) at libusb:001:005
$ scanimage -L
device `epkowa:interpreter:001:005' is a Epson (unknown model) flatbed scanner
$ ls /proc/bus
input  pci

```
When I launch xsane or iscan, I get "access refused to the peripheral".

---

### Post by dargaud on 2011-07-03
Sorry folks, just turning the scanner off and back on solved it. It must be the 1st time, when installing the driver while the scanner was already on.

---

