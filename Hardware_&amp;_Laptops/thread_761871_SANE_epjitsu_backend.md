---
title: "SANE epjitsu backend"
date: 2008-04-21
forum: Hardware &amp; Laptops
---

### Post by jojuez on 2008-04-21
I am beating my head against a wall here. I am trying to use sane with a Fujitsu Scansnap S300. As of 1.0.19 of SANE, it is supposed to be supported for basic functionality. By default there was no epjitsu.conf file in my sane.d dir after installing SANE. I was able to find a sample config and put it in there. I am able to find the scanner using sane-find-scanner, but it says no device found when I do a scanimage -L. Any help would be greatly appreciated. Thank you in advance.

---

### Post by eddyanm on 2008-04-24
I just got mine working just yesterday on Feisty with sane-backend 1.0.19.

You need to get the firmware .nal file (eg. 300_0C00.nal) by installing the Windows software and search for the file in your C:\Windows folder.  Then configure the conf file to point to it.

Also, it's a good idea to download the backend source, compile it, it will generate the udev rule file so the proper permission is set when you plug in your scanner. Copy the rule file from the source's tools directory to your /etc/udev/rules.d directory. The conf file is also available in the source tree.  Otherwise, you will need to set the permission of the usb device /proc/bus/usb/0xx/0xx every time you plug the scanner in.

---

