---
title: "Problem with USB modem"
date: 2020-03-24
forum: Hardware
---

### Post by chlansky on 2020-03-24
[SIZE=2][FONT=arial]HiI have a problem with the ZTE MF821 USB modem. After some time it disappears from the system and even restarting does not help. Only pulling out and putting into the same port helps.
[/FONT][/SIZE]
[FONT=arial]My version is Ubuntu 16.04 LTS, a modem used as a sms gateway (gammu, playsms).[/FONT]
[SIZE=2]
Result of the lsusb command[/SIZE]

```
lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
ls -l /dev/ttyU*
ls: cannot access '/dev/ttyU*': No such file or directory

```

dmesg
```
[ 7578.032177] option 2-4:1.0: GSM modem (1-port) converter detected
[ 7578.032290] usb 2-4: USB disconnect, device number 2
[ 7578.032301] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[ 7578.032336] option 2-4:1.1: GSM modem (1-port) converter detected
[ 7578.032394] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[ 7578.032425] option 2-4:1.2: GSM modem (1-port) converter detected
[ 7578.032482] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB2
[ 7578.032514] option 2-4:1.3: GSM modem (1-port) converter detected
[ 7578.032569] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB3
[ 7578.032764] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 7578.032774] option 2-4:1.0: device disconnected
[ 7578.032866] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 7578.032875] option 2-4:1.1: device disconnected
[ 7578.032964] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 7578.032972] option 2-4:1.2: device disconnected
[ 7578.033070] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[ 7578.033079] option 2-4:1.3: device disconnected
[ 7578.200027] usb 2-4: new high-speed USB device number 3 using ehci-pci
[ 7583.312018] usb 2-4: device descriptor read/64, error -110
[ 7598.528018] usb 2-4: device descriptor read/64, error -110
[ 7598.744023] usb 2-4: new high-speed USB device number 4 using ehci-pci
[ 7603.856017] usb 2-4: device descriptor read/64, error -110
[ 7619.072023] usb 2-4: device descriptor read/64, error -110
[ 7619.176041] usb usb2-port4: attempt power cycle
[ 7619.596018] usb 2-4: new high-speed USB device number 5 using ehci-pci
[ 7630.004023] usb 2-4: device not accepting address 5, error -110
[ 7630.116022] usb 2-4: new high-speed USB device number 6 using ehci-pci
[ 7640.524022] usb 2-4: device not accepting address 6, error -110
[ 7640.524093] usb usb2-port4: unable to enumerate USB device
[ 7640.776022] usb 7-2: new full-speed USB device number 2 using uhci_hcd
[ 7655.888030] usb 7-2: device descriptor read/64, error -110
[ 7671.104019] usb 7-2: device descriptor read/64, error -110
[ 7671.320023] usb 7-2: new full-speed USB device number 3 using uhci_hcd
[ 7686.432019] usb 7-2: device descriptor read/64, error -110
[ 7701.648017] usb 7-2: device descriptor read/64, error -110
[ 7701.752029] usb usb7-port2: attempt power cycle
[ 7702.172017] usb 7-2: new full-speed USB device number 4 using uhci_hcd
[ 7712.580022] usb 7-2: device not accepting address 4, error -110
[ 7712.692018] usb 7-2: new full-speed USB device number 5 using uhci_hcd
[ 7723.100021] usb 7-2: device not accepting address 5, error -110
[ 7723.100090] usb usb7-port2: unable to enumerate USB device
[ 9538.658046] perf interrupt took too long (2510 > 2500), lowering kernel.perf_event_max_sample_rate to 50000

```[FONT=arial]My version is Ubuntu 16.04 LTS, a modem used as a sms gateway (gammu, playsms).[/FONT]

---

