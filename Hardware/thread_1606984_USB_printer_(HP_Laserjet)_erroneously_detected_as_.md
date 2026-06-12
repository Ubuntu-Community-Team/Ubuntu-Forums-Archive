---
title: "USB printer (HP Laserjet) erroneously detected as parallel"
date: 2010-10-27
forum: Hardware
---

### Post by skillet-thief on 2010-10-27
Hello (first post to these forums, hope I'm in the right place),

I have an HP Laserjet 1320 that had been working fine for years on an Ubuntu box, including all the way up to Maverick. I'm switching to a new box, also with Maverick, and can't get the printer to show up as a usb device. Instead, a parallel port shows up. Attempts to install/print via the parallel port have failed.

```
Oct 27 05:48:31 rosario kernel: [ 1488.694870] usb 2-1.4: USB disconnect, address 3
Oct 27 05:48:40 rosario kernel: [ 1497.098629] usb 2-1.3: new full speed USB device using ehci_hcd and address 6
Oct 27 05:48:40 rosario kernel: [ 1497.338015] parport1: fix this legacy no-device port driver!
Oct 27 05:48:40 rosario kernel: [ 1497.338224] lp1: using parport1 (polling).

```On the other install, the printer's URI was hp:/usb/hp_LaserJet_1320_series, but on the new box all I have in /dev/usb/ is

```
joseph@rosario:~$ ls -l /dev/usb
total 0
crw------- 1 root root 180, 96 2010-10-27 05:23 hiddev0
crw------- 1 root root 180, 97 2010-10-27 05:23 hiddev1
crw------- 1 root root 180, 98 2010-10-27 05:23 hiddev2
crw------- 1 root root 180, 99 2010-10-27 05:23 hiddev3
```I've fixed the dependencies in for the hplip tools, but that doesn't seem to matter anyway since they never detect anything as connected via usb... 

Here is some relevant lsmod output. Oddly enough, these are all about the same as on the other box where everything worked. So I am stumped.

```
joseph@rosario:~$ lsmod | grep parp
parport_pc             30086  0 
parport                37032  4 parport_pc,ppdev,uss720,lp

``````
oseph@rosario:~$ lsmod | grep usb
usblp                  12700  0 
rt2x00usb              11316  1 rt2800lib
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
mac80211              266657  3 rt2x00usb,rt2x00pci,rt2x00lib
usb_storage            50372  0 
usbhid                 42062  0 
hid                    84678  1 usbhid
```Any help and/or suggestions will be greatly appreciated!

---

### Post by skillet-thief on 2010-10-28
I've read that the uss720 module, which shows up, is responsible for converting a USB connection to a parallel port connection. If I could somehow prevent that from happening I think I would be able to solve all of my problems.

---

### Post by skillet-thief on 2010-11-08
This has solved itself. All it took was a reboot... It seems that reboots are becoming more and more necessary to keep everything working correctly, and it isn't limited to just Ubuntu. Anyway, all is better now, I have a shiny "HP" logo in the taskbar and everything seems to work.

(Going to try to mark this as solved...)

---

