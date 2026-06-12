---
title: "Ralink RT5370 wireless usb adapter stops working with vendor request 0x0[67] failed"
date: 2023-01-25
forum: Hardware
---

### Post by kenga13 on 2023-01-25
Ralink RT5370 wireless usb adapter stops working with vendor request 0x0[67] failed error on Ubuntu 22.04LTS mainstream kernel (and, on previous releases too - 18.04,20.04), if some network load happens. Is there any solution, f.e. some another branch kernel, firmware or alternative driver?

```
/var/log/syslog.1:Jan 24 18:29:42 mrouter03 kernel: [31167.382430] ieee80211 phy24: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1700 with error -110
/var/log/syslog.1:Jan 24 18:29:49 mrouter03 kernel: [31174.104207] ieee80211 phy24: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0218 with error -110
/var/log/syslog.1:Jan 24 18:29:49 mrouter03 kernel: [31174.164146] ieee80211 phy24: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x021c with error -110

```
Also, warnings sometimes

```
/var/log/syslog.1:Jan 24 18:59:24 mrouter03 kernel: [  229.704877] ieee80211 phy0: rt2800_txdone: Warning - Data pending for entry 15 in queue 2
/var/log/syslog.1:Jan 24 19:00:25 mrouter03 kernel: [  290.654902] ieee80211 phy0: rt2800_txdone: Warning - Data pending for entry 13 in queue 2

```

```

rmmod rt2800usb
modprobe rt2800usb

``` helps for some time, then problem repeats.

```
 
# lsusb | grep 5370 | grep -v grep
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

# dmesg | grep -E '(usb 1-1|phy[0-9]|5370)'
[    3.375263] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    3.771406] usb 1-1: New USB device found, idVendor=148f, idProduct=5370, bcdDevice= 1.01
[    3.772126] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.802128] usb 1-1: Product: 802.11 n WLAN
[    3.832815] usb 1-1: Manufacturer: Ralink
[    3.862589] usb 1-1: SerialNumber: 1.0
[   23.426118] usb 1-1: reset high-speed USB device number 2 using ehci-pci
[   23.816759] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   24.273559] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
[   24.275621] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   31.708413] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   31.719186] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36

```

---

### Post by laiti on 2023-04-27
I'm having the same issue. I have a very cheap and small USB wlan adapter and apparently it is RT5370 based:


```
$ sudo dmesg | grep -E '(usb 3-2|phy[0-9]|5370)'
[    1.444285] usb 3-2: new high-speed USB device number 2 using xhci_hcd
[    1.610006] usb 3-2: New USB device found, idVendor=148f, idProduct=5370, bcdDevice= 1.01
[    1.610017] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.610020] usb 3-2: Product: 802.11 n WLAN
[    1.610023] usb 3-2: Manufacturer: Ralink
[    1.610026] usb 3-2: SerialNumber: 1.0
[   38.120613] usb 3-2: reset high-speed USB device number 2 using xhci_hcd
[   38.286908] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   38.297601] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
[   38.297745] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   38.347870] rt2800usb 3-2:1.0 wlx243c2009181e: renamed from wlan0
[   52.953989] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   53.348536] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  282.683900] ieee80211 phy0: rt2800_txdone: Warning - Data pending for entry 5 in queue 2
[  282.683937] ieee80211 phy0: rt2800_txdone: Warning - Data pending for entry 5 in queue 2
```

But as it is cheap and in an USB slot, I could as well replace it with something better. Any suggestions?

---

