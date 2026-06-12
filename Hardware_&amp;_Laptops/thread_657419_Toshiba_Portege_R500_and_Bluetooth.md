---
title: "Toshiba Portege R500 and Bluetooth"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by k999 on 2008-01-03
Hi,

I have a Toshiba Portege R500-11B with Ubuntu 7.10 - The Gutsy Gibbon - on it. I was starting to wonder whether it had bluetooth at all until I discovered I had to switch it on with this command:

```
sudo /usr/bin/toshset -bluetooth on
```

Now I am trying to connect it to my phone, but without much luck. This is what I am seeing:

```
$ hcitool scan
Scanning ...
Inquiry failed: Device or resource busy
$ hcitool scan
Scanning ...
        00:16:AA:BB:CC:DD       PhoneName
$ hcitool cc 00:16:AA:BB:CC:DD
Can't create connection: Operation not permitted
$ sudo hcitool lq 00:16:AA:BB:CC:DD
Not connected.
$ sudo hcitool cc 00:16:AA:BB:CC:DD
Can't create connection: Input/output error
$ sudo hcitool cc 00:16:AA:BB:CC:DD
$ sudo hcitool lq 00:16:AA:BB:CC:DD
Link quality: 255
$ sudo hcitool lq 00:16:AA:BB:CC:DD
Not connected.
$ 
```

These commands were all run in fairly rapid succession, no long waits. The phone was discoverable during the entire ordeal. It appears that the connection I create with hcitool cc is broken almost immediately, which obviously isn't what I want...

Relevant lines from /var/log/syslog are:

```
Jan  3 22:30:50 toshiba-laptop NetworkManager: <debug> [1199395850.803824] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_930_508_noserial_if0_bluetooth_hci_bluetooth_hci'). 
Jan  3 22:30:55 toshiba-laptop NetworkManager: <debug> [1199395855.872084] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_930_508_noserial_if0_bluetooth_hci_bluetooth_hci'). 
Jan  3 22:31:02 toshiba-laptop NetworkManager: <debug> [1199395862.824290] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_930_508_noserial_if0_bluetooth_hci_bluetooth_hci'). 
Jan  3 22:31:08 toshiba-laptop NetworkManager: <debug> [1199395868.679121] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_930_508_noserial_if0_bluetooth_hci_bluetooth_hci'). 

```

Is it hal that is killing my connection for some reason?

---

