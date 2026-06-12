---
title: "Epson Perfection 3170 Scanner Permissions in Elementary"
date: 2014-11-16
forum: Hardware
---

### Post by JimmyJames89 on 2014-11-16
Hi folks... 

I've been pulling out the few strands of hair left trying to get this scanner to work. 

I've followed how-to here: 

[http://askubuntu.com/questions/49389/running-a-epson-scanner-perfection-3170](http://askubuntu.com/questions/49389/running-a-epson-scanner-perfection-3170)

And information about "epkowa" drivers that seem like they should do the trick but I'm not sure if they're installed :S

Sane-find-scanner:

```
found USB scanner (vendor=0x04b8, product=0x0116) at libusb:001:007

```

I'm using the latest Elementary OS Distro and it seems I get stumped when trying to add permission for my user to the scanner. In any how to for the scanner it says to add permission: 


> [COLOR=#333333][FONT=UbuntuRegular]15)Add yourself to the scanner group (adding the scanner group if needed)
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]System > Administration > Users and Groups > manage groups > unlock > add > check self[/FONT][/COLOR]

I can't find this menu or any variant of it. Is there a command line or file I can edit? 

I got real close to having this scanner working until I hit a 32bit scanner/64 bit conflict (different machine). 

I've unplugged any potentially conflicting devices - Hauppage DVR and Philips Wifi USB (sane-find-scanner saw the WiFi dongle as a scanner...)

Aaaaaand I just did a reboot (without posting or saving the contents of this message first. Thanks auto-save!) to no avail. 

Heeeeeeeeeellllp!

---

### Post by houstonbofh on 2014-11-16
fropm the cli type "more /etc/groups | grep" username and it will show what groups you are in.  There is no "scanner" group in default Ubuntu, so I am not sure what you will need.  (Never used Elementary OS)

---

### Post by pqwoerituytrueiwoq on 2014-11-16
In ubuntu you need to be part of the lp group to use a scanner
does this show your scanner?
```
scanimage -L
sudo scanimage -L
```
have you found a 64bit driver?
if not you will need to compile there driver from this file: iscan_2.10.0-1.tar.gz
im gonna try to (edit: it errored on me)

---

### Post by JimmyJames89 on 2014-11-16
```

james@JDesk:~$ scanimage -L


No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
james@JDesk:~$ sudo scanimage -L
device `epson:libusb:001:002' is a Epson  flatbed scanner
```

```

james@JDesk:~$ more /etc/groups | grep james
/etc/groups: No such file or directory

```

I bailed on the 64 bit and am using a 32bit system to load this scanner. 

the lp group? I added the scanner module as per instructions in /etc/sane.d/epkowa.conf

epkowa.conf: 

```
# epkowa.conf -- sample configuration for the EPKOWA SANE backend
# Copyright (C) 2004  Olaf Meeuwissen
#
# See sane-epkowa(5), sane-scsi(5) and sane-usb(5) for details.


# SCSI scanners can be configured simply by listing the path to the
# device.  For example, if your system claims to have a /dev/scanner
# SCSI device, all you have to do is uncomment the following line:
#
#/dev/scanner
#
# In the interest of maintainability, most installations would have
# /dev/scanner sym-linked to the real SCSI scanner device node.
#
# An alternative way that works for many operating systems and is a
# little bit more generic, is to have the backend probe for your SCSI
# scanner with the following configuration command:
#
scsi EPSON


# On systems with libusb, the following line is sufficient to get the
# backend to recognise your USB scanners.  It presumes, however, that
# the scanner---more precisely, it's USB product ID---is known to the
# backend.
# For all USB scanners that are officially supported by this backend,
# this presumption is true.  A list of such scanners can be found in
# sane-epkowa(5).
#
#usb


# For any USB scanner not known to the backend (yet), you may, at your
# own peril(!!), force the backend to recognise and use it via libusb.
# You can do so by the following configuration command:
# 
#   usb <USB vendor ID> <USB product ID>
#
# SEIKO EPSON's USB vendor ID is '0x04b8' (without quotes).  In order
# to find the USB product ID, use lsusb(1) or, on Linux systems, peek
# at the information in /proc/bus/usb/devices.
# A sample configuration for the Perfection 1650 (GT-8200), which has
# a product ID of 0x0110, would look as follows:
#
#usb 0x04b8 0x0110


# When not accessing your USB scanner via libusb, you may need to use
# one of the configuration commands below or commands that are almost
# the same.  These commands typically access the scanner via a kernel
# scanner module.
#
#usb /dev/usb/scanner0
#usb /dev/usbscanner0
#usb /dev/uscanner0
usb /dev/bus/usb/001
#
# Linux had a scanner module until version 2.6.2.  As of version 2.6.3
# libusb is your only option.  Linux' scanner module can be loaded via
# the modprobe(8) command like so:
#
#   modprobe scanner vendor=<USB vendor ID> product=<USB product ID>
#
# If the scanner module already knows the vendor and product IDs, you
# do not have to specify them.  If you want to have this done automa-
# tically every time you boot, you can add the above line, except for
# the modprobe command itself, to your /etc/modules file.


# Although not tested with this backend, parallel port scanners should
# be usable.  You can configure them as shown below, but I do not know
# much about the details.  Information is welcome.
#
#pio 0x278
#pio 0x378
#pio 0x3BC
usb 0x04b8 0x0116
```

I've tried the modprobe command, the reply is FATAL module not loaded. 
I've added the line "scanner vendor=04b8 product=0116" into /etc/modules and rebooted - nada (the only other item in this file is "lp" - the group [COLOR=#000000]pqwoerituytrueiwoq mentioned. [/COLOR]
The libusb things mentioned are lost on me.

Hope posting that file wasn't too verbose :P I'm new here - have been using linux a while but I have just started to get a bit more involved. 

Thanks for the insights guys. This scanner will work if it's the death of me... 

I'm sure most linux users have died that way.

---

### Post by pqwoerituytrueiwoq on 2014-11-16
for one of my scanner to work from www-data i have to have this file,perhaps you need to do this for your main user account to work
```
cat  /etc/udev/rules.d/40-scanner.rules
SUBSYSTEMS=="usb", ATTRS{idVendor}=="**1606**", ATTRS{idProduct}=="**0060**", ENV{libsane_matched}="yes", GROUP="lp"
~$ lsusb|grep Umax
Bus 003 Device 040: ID **1606**:**0060** Umax Astra 3400/3450
```

for the sake of science can you try my php scanner server (see signature) and see if it is usable from it?
since the driver is present it should in theory
let me know if it gives any errors
if it works you get a sweet scanner ui

aside: If anyone is wondering how i got that scanner model working, it only 1/2 works, the driver is buggy on this model or the hardware is failing (and if anyone wants to say just use windows that thing only has drivers for xp)

---

### Post by JimmyJames89 on 2014-11-16
Okay, so, I've made the file [COLOR=#000000][FONT=Ubuntu Mono]/etc/udev/rules.d/40-scanner.rules[/FONT][/COLOR]
```
cat  /etc/udev/rules.d/40-scanner.rules
SUBSYSTEMS=="usb", ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0116", ENV{libsane_matched}="yes", GROUP="lp"
~$ lsusb|grep Seiko
Bus 001 Device 002: ID 04b8:0116 Seiko Epson Corp. Perfection 3170 (GT-9400)

```

The tutorial quoted above also advised adding this file - 50-libsane-extras.rules

```
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0116", MODE="0666", GROUP="scanner"
13)
```

I might remove that one and reboot. hmm. 

The PHP printer server? I'm sorry that goes a bit over my head. I have a tower and switch sitting here waiting for me to install my first Debian Home server, but it's a bit too late in the afternoon to start tinkering with that!

---

### Post by pqwoerituytrueiwoq on 2014-11-17
it can run along side your desktop install, the lazy install script can set everything up then follow a few instructions in your web browser
of course if it does work you could set it up on that server yuo have yet to setup and use a 64bit install on your main system, while the 32bit ones runs on that server with the scanner
the scripts should work on any modern Debian based system, i have tested it on ubuntu 10.04,12.04,12.10, 13.04,14.04, and raspbian

if the rulse i posted does not work try this one
```
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0116", MODE="0666", GROUP="lp"
```

---

### Post by JimmyJames89 on 2015-01-04
Sorry about the delay in my reply... 

I have since rejigged and reinstalled numerous things since and hence gave up. I have a Windows 7 laptop around to handle hardware like that. 

I've bookmarked your scanner server script. On the if and when I get it up and running I might post a tutorial.

---

### Post by JimmyJames89 on 2015-01-29
SOLVED!

I have been trying since last August, the solution was only found two months ago:
[http://askubuntu.com/questions/548639/running-a-epson-scanner-perfection-3170-in-ubuntu-14-04](http://askubuntu.com/questions/548639/running-a-epson-scanner-perfection-3170-in-ubuntu-14-04)

SANE Developers:
[http://lists.alioth.debian.org/pipermail/sane-devel/2014-November/032889.html](http://lists.alioth.debian.org/pipermail/sane-devel/2014-November/032889.html)

I still get a lot of udev errors on boot - it's not a perfect install, but I can scan! 

[http://imgur.com/jUagj0l](http://imgur.com/jUagj0l)

---

