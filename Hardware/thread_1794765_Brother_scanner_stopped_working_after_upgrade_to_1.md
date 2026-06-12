---
title: "Brother scanner stopped working after upgrade to 11.04"
date: 2011-07-01
forum: Hardware
---

### Post by luisito on 2011-07-01
I have a Brother MFC J630W working over wifi, which is a multifunction device including printer and scanner. It used to work very well until I upgraded to 11.04 a few months ago.

The printer still works and has always been working well. The scanner part is what does not.

Right after the upgrade, it would not identify the device. Then I reinstalled the driver from Brother's website and now it does see it, but it doesn't work.

When I try 
[INDENT]brsaneconfig3 -q[/INDENT]
I get
[INDENT]Devices on network
  0 SCANNER             "MFC-J630W"         I:193.168.1.66
[/INDENT]

When I try
[INDENT]brscan-skey -l
[/INDENT]
I get
[INDENT]SCANNER           : brother3:net1;dev0  : 193.168.1.66         Not responded[/INDENT]

When I try
[INDENT]simple-scan -d[/INDENT]
and I try to scan, I get

[INDENT]** (simple-scan:2924): DEBUG: Starting Simple Scan 2.32.0.1, PID=2924
** (simple-scan:2924): DEBUG: Restoring window to 600x400 pixels
** (simple-scan:2924): DEBUG: sane_init () -> SANE_STATUS_GOOD
** (simple-scan:2924): DEBUG: SANE version 1.0.22
** (simple-scan:2924): DEBUG: Requesting redetection of scan devices
** (simple-scan:2924): DEBUG: Processing request
** (simple-scan:2924): DEBUG: sane_get_devices () -> SANE_STATUS_GOOD
** (simple-scan:2924): DEBUG: Device: name="brother3:net1;dev0" vendor="Brother" model="MFC-J630W" type="SCANNER"
** (simple-scan:2924): DEBUG: Requesting scan at 75 dpi from device 'brother3:net1;dev0'
** (simple-scan:2924): DEBUG: scanner_scan ("brother3:net1;dev0", 75, SCAN_SINGLE)
** (simple-scan:2924): DEBUG: Processing request[/INDENT]
and the whole thing gets stuck

When I try xsane, a small window saying "scanning for devices" shows up, then it closes, and nothing happens.

I am trying to scan from my laptop, which is a Thinkpad X201 Tablet with Ubuntu 11.04.

---

