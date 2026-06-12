---
title: "Broadcom Corporation BCM44312 802.11b/g LPP-PHY (rev 01)"
date: 2015-09-21
forum: Hardware
---

### Post by Tonyslav on 2015-09-21
Hi everybody! I'm reporting a bug with the latest kernel 4.2.0 and the p[FONT=arial]ackage: bcmwl-kernel-source 6.30.223.248+bdcom-0ubuntu2[/FONT]. After upgrading to kernel 4.2.0, the wi-fi card (Dell Wireless Wlan Mini-Card) of my Dell Inspiron 1525 is not working. Can't turn it on. I had bc43-fwcutter & firmwarre-b43-installer packages installed and everything was ok 'til the upgrade. Any suggestions or solutions will be needed. ):P



Launchpad bug report link >> [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1498153](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1498153)

---

### Post by Tonyslav on 2015-09-21
Fix for my friends who expirienced this problem:
[COLOR=#111111][FONT=Ubuntu]Uninstall the bcmwl-kernel-source package by issuing the following command on a terminal:[/FONT][/COLOR]
sudo apt-get remove bcmwl-kernel-source
[COLOR=#111111][FONT=Ubuntu]make sure that the firmware-b43-installer and the b43-fwcutter packages are installed (of course you will need internet by others means):[/FONT][/COLOR]
sudo apt-get install firmware-b43-installer b43-fwcutter
[COLOR=#111111][FONT=Ubuntu]type into terminal:[/FONT][/COLOR]
cat /etc/modprobe.d/* | egrep 'bcm'
[COLOR=#111111][FONT=Ubuntu](you may want to copy this) and see if the term 'blacklist bcm43xx' is there[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]if it is, type cd /etc/modprobe.d/ and then sudo gedit blacklist.conf[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]put a # in front of the line: blacklist bcm43xx[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]reboot[/FONT][/COLOR]

---

