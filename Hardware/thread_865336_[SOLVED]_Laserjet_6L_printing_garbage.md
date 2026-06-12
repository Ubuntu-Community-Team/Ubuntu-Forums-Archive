---
title: "[SOLVED] Laserjet 6L printing garbage"
date: 2008-07-20
forum: Hardware
---

### Post by paddy1 on 2008-07-20
I just installed an HP Laserjet 6L in Ubuntu 8.04, installed all updates, configured the printer to the recommended driver (HP LaserJet 6L Foomatic/ljet4 (recommended)). It prints out garbage, and just keeps right on going until you remove the paper.

This is the contents of /etc/hp file

# hplip.conf.  Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.8.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-doc/HTML
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
internal-tag=2.8.2.10# hplip.conf.  Generated from hplip.conf.in by configure.

---

### Post by arcticblue on 2008-10-26
Solved how?

---

