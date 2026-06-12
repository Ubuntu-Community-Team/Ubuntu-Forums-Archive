---
title: "HUAWEI E1762 3G USB on 12.04"
date: 2013-03-08
forum: Hardware
---

### Post by dcstar on 2013-03-08
I recently got one of these devices and unfortunately it does not seem to be auto-detected on my 12.04 system (using Gnome 3) for Mobile Broadband use, but after a lot of research I finally got it working.

For anyone else who has a similar issue, here are the steps I used to get it going:

[LIST=1]
[*]Plug the device into your USB port, give it 10 seconds or so to settle and then run this in a terminal:
```
lsusb
```
[*]Find the line that looks similar to this and note the "ID" data:
```
Bus 002 Device 005: ID **12d1:140c **Huawei Technologies Co., Ltd.
```
[*]Download and install the sakis3g tool:
[http://wiki.sakis3g.org/wiki/index.php?title=Main_Page](http://wiki.sakis3g.org/wiki/index.php?title=Main_Page)


[*]Do this to create a default configuration file:
```
sudo gedit /etc/sakis3g.conf
```
[*]Paste the following into this file, modify it for your ISP and USB ID device settings and then save it:
```
--nostorage
--pppd
APN="CUSTOM_APN"
CUSTOM_APN="*your custom APN*"
APN_USER="*your user name*"
APN_PASS="*your password*"
USBINTERFACE="0"
USBDRIVER="option"
OTHER="USBMODEM"
USBMODEM="**12d1:140c**"
```
[*]Run the saskis3g program (from where-ever you downloaded it to) and choose the "Connect" selection.
[*]You should now have a 3G connection!
[*]Use the option to create a Desktop Shortcut to launch it.
[/LIST]
I got this working on the Exetel ISP in Australia using an Optus USB modem - as they are just resellers of this network.

Please note that using this **sakis3g** script will disable any DNS settings on other network connections when you disconnect from the 3G service. Simply disable and re-enable networking to fix things back up.

---

