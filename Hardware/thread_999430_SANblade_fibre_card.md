---
title: "SANblade fibre card"
date: 2008-12-01
forum: Hardware
---

### Post by mprime on 2008-12-01
Hello all,

I have the task of configuring a Ubuntu 7.04 system to utilise a QMC2462S Fibre card that runs to a SAN. I have a very limited understanding of how a SAN works but have been told I must install drivers to support multipathing.

I found some instructions for a redhat server and proceeded to convert the rpm packages to deb packages. Below is a list of the packages that I installed. 

debhelper_5.0.42ubuntu1_all.deb
dpkg-dev_1.13.24ubuntu6_all.deb
gettext_0.16.1-1ubuntu2_i386.deb
html2text_1.3.2a-3_i386.deb
intltool-debian_0.35.0+20060710.1_all.deb
po-debconf_1.0.8_all.deb
qla2x00-source_8.00.02-3_all.deb

The issue is that while these packages install fine I still don't see the fibre card when running
"/usr/sbin/datapath query device"

Any help and advice would be greatly appriciated.

Mprime

---

