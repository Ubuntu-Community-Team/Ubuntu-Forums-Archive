---
title: "Cant print on usb Epson LX300"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by tatodc on 2009-07-25
Hi,
I just setup a new ubuntu server v9.04m installed cups for my to printers to work over the network. The HP one works fine, but not the Epson LX 300.

It is recognized by the OS since the usblp1 file is created, but when I try to have it recognized by cups, it just doesn't show.

Took out the HP for debuging...

output from lsusb:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 04b8:0005 Seiko Epson Corp. Stylus D88+
Bus 002 Device 003: ID 0e0f:0002
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

output from lpinfo -v:
network ipp
network socket
network lpd
direct scsi
network http
direct parallel:/dev/lp0
direct hp

---

