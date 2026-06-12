---
title: "Ch352 pci rs232 interface need help"
date: 2008-08-14
forum: Hardware
---

### Post by angelo-castiglione on 2008-08-14
Hi to all,

I looking for help to install driver in Ubuntu of my PCI RS232 INTERFACE called CH352. I have also original CD-ROM with driver for LINUX.

This PCI interface add n° 2 RS232 DB9 to my pc.

Anywone can help me ?


Thanks in advance

Angelo

---

### Post by kkkaren on 2009-03-21
In Ubuntu 8.04 Hardy install 
*********************************************
<1>-copy install_ss_80x86.o to /usr/sbin
<2>-Add text /usr/sbin/install_ss_80x86 to rc.local (path /etc/rc.local)
<3>-reboot

rc.local file example
_______________________________-
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
 /usr/sbin/install_ss_80x86
exit 0

---

