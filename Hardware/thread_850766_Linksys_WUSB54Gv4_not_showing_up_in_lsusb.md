---
title: "Linksys WUSB54Gv4 not showing up in lsusb"
date: 2008-07-05
forum: Hardware
---

### Post by stratcat50 on 2008-07-05
Dual booting xp/ubuntu 8.0.4 on an IBM XServer 205. Latest BIOS.
WUSB works in xp, not in Linux .
Naturally, ndiswrapper doesn't work as a result.
The LED on WUSB comes on for a few seconds when plugged in, then goes
out. Possible usb overcurrent? How to disable?
Any suggestions? 
(Yes, I know that usb networking is WRONG but I'd like to try it.)

lsusb
Bus 003 Device 006: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Shows the flashdrive but not the WUSB. Plugging the WUSB into another USB port has similar results.

tail -f /var/log/messages shows this when the device is plugged in:

Jul  5 21:56:07 fneeb kernel: [ 7243.921596] usb 3-1: new high speed USB device using ehci_hcd and address 19
<several more times with 'address xx' incrementing>

---

### Post by Kangarooo on 2010-05-05
heres also this camera
[http://ubuntuforums.org/showthread.php?t=1442626](http://ubuntuforums.org/showthread.php?t=1442626)

---

