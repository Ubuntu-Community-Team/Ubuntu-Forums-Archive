---
title: "USB Modem"
date: 2010-09-03
forum: Hardware
---

### Post by pi.theta on 2010-09-03
I have a USB 3G Modem (Teracm LW272) which I use to connec to the internet. Every time the AC power goes out, and my laptop switches to battery or vice versa, the pppd connection gets disrupted or the modem gets disconected. I am using Arch Linux on a Dell Inspiron 1520. Could this be a hardware problem with the modem?
Apoorv

---

### Post by pi.theta on 2010-09-04
Somewhen please help. This is causing a huge problem, as there is a electricity problem in my hostel.

The dmesg output during this anomaly is:
```

usb 2-1: new high speed USB device using ehci_hcd and address 7
scsi9 : usb-storage 2-1:1.0
usb 2-1: USB disconnect, address 7
usb 2-1: new high speed USB device using ehci_hcd and address 8
option 2-1:1.0: GSM modem (1-port) converter detected
usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
option 2-1:1.1: GSM modem (1-port) converter detected
usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
option 2-1:1.2: GSM modem (1-port) converter detected
usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
option 2-1:1.3: GSM modem (1-port) converter detected
usb 2-1: GSM modem (1-port) converter now attached to ttyUSB3
scsi10 : usb-storage 2-1:1.4
scsi 10:0:0:0: Direct-Access     HSPA     MMC Storage      2.31 PQ: 0 ANSI: 2
sd 10:0:0:0: Attached scsi generic sg2 type 0
sd 10:0:0:0: [sdb] Attached SCSI removable disk
PPP generic driver version 2.4.2
CE: hpet increased min_delta_ns to 7500 nsec
ata1.00: configured for UDMA/133
ata1: EH complete
sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
ata1: hard resetting link
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata1.00: configured for UDMA/133
ata1: EH complete
usb 2-1: USB disconnect, address 8
option: option_instat_callback: error -108
option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
option 2-1:1.0: device disconnected
option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
option 2-1:1.1: device disconnected
option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
option 2-1:1.2: device disconnected
option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
option 2-1:1.3: device disconnected
ADDRCONF(NETDEV_UP): wlan0: link is not ready
usb 2-1: new high speed USB device using ehci_hcd and address 9
option 2-1:1.0: GSM modem (1-port) converter detected
usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
option 2-1:1.1: GSM modem (1-port) converter detected
usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
option 2-1:1.2: GSM modem (1-port) converter detected
usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
option 2-1:1.3: GSM modem (1-port) converter detected
usb 2-1: GSM modem (1-port) converter now attached to ttyUSB3
scsi11 : usb-storage 2-1:1.4
scsi 11:0:0:0: Direct-Access     HSPA     MMC Storage      2.31 PQ: 0 ANSI: 2
sd 11:0:0:0: Attached scsi generic sg2 type 0
sd 11:0:0:0: [sdb] Attached SCSI removable disk
ata1: hard resetting link
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata1.00: configured for UDMA/133
ata1: EH complete
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
ata1.00: configured for UDMA/133
ata1: EH complete
usb 2-1: USB disconnect, address 9
option: option_instat_callback: error -108
option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
option 2-1:1.0: device disconnected
option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
option 2-1:1.1: device disconnected
option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
option 2-1:1.2: device disconnected
option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
option 2-1:1.3: device disconnected
usb 2-1: new high speed USB device using ehci_hcd and address 10
option 2-1:1.0: GSM modem (1-port) converter detected
usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
option 2-1:1.1: GSM modem (1-port) converter detected
usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
option 2-1:1.2: GSM modem (1-port) converter detected
usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
option 2-1:1.3: GSM modem (1-port) converter detected
usb 2-1: GSM modem (1-port) converter now attached to ttyUSB3
scsi12 : usb-storage 2-1:1.4

```

The modem seems to work fine on windows xp. So most probably this a usb power management problem.

Regards,
Apoorv

---

### Post by pi.theta on 2010-09-05
Can't anyone identify what error code -108 refers to?
```
option: option_instat_callback: error -108
```

---

### Post by max5555 on 2010-12-12
Try the following solution: [Network-manager auto-reconnect [SOLVED]]("http://best-ubuntu-notebook.blogspot.com/2010/12/network-manager-auto-reconnect-solved.html")

---

