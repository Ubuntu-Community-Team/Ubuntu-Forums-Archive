---
title: "Xubuntu 14.04 bluetooth not able to see/setup any devices"
date: 2015-01-05
forum: Hardware
---

### Post by dentaku65 on 2015-01-05
Hi,

I've reinstalled from scratch Xubuntu 14.04 but I have an issue with bluetooth; the system recognized my device, but when I tried to setup a device I'm not find any in the wizard, on my side seems that everything is ok:

```
dmesg | grep -i blue
[   13.646587] Bluetooth: Core ver 2.17
[   13.646619] Bluetooth: HCI device and connection manager initialized
[   13.646632] Bluetooth: HCI socket layer initialized
[   13.646637] Bluetooth: L2CAP socket layer initialized
[   13.646645] Bluetooth: SCO socket layer initialized
[   16.489855] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.489862] Bluetooth: BNEP filters: protocol multicast
[   16.489877] Bluetooth: BNEP socket layer initialized
[   16.512888] Bluetooth: RFCOMM TTY layer initialized
[   16.512908] Bluetooth: RFCOMM socket layer initialized
[   16.512918] Bluetooth: RFCOMM ver 1.11
```
```
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: samsung-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
```
```
hciconfig --all
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 50:B7:C3:CD:9E:DF  ACL MTU: 1022:8  SCO MTU: 183:5
    UP RUNNING PSCAN 
    RX bytes:1769 acl:0 sco:0 events:131 errors:0
    TX bytes:2527 acl:0 sco:0 commands:107 errors:0
    Features: 0xff 0xfe 0x0d 0xfe 0xd8 0x7f 0x7b 0x8f
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'xubuntu-0'
    Class: 0x740100
    Service Classes: Rendering, Object Transfer, Audio, Telephony
    Device Class: Computer, Uncategorized
    HCI Version:  (0x7)  Revision: 0x1102
    LMP Version: 4.0 (0x6)  Subversion: 0x1
    Manufacturer: Atheros Communications, Inc. (69)
```
```
ps -A |grep blue
690 ?        00:00:00 bluetoothd
 1663 ?        00:00:00 blueman-applet
```
Can someone give me an hint in order to connect the devices via bluetooth?

TIA
Den

---

### Post by jeremy31 on 2015-01-05
> **dentaku65 said:**
> Hi,

I've reinstalled from scratch Xubuntu 14.04 but I have an issue with bluetooth; the system recognized my device, but when I tried to setup a device I'm not find any in the wizard, on my side seems that everything is ok:

```
dmesg | grep -i blue
```

```
rfkill list all
```

```
hciconfig --all
```

```
ps -A |grep blue
```

Can someone give me an hint in order to connect the devices via bluetooth?

TIA
Den

I do need some more info ```
lsusb
``````
dmesg | grep firmware
``````
uname -a
```

---

### Post by dentaku65 on 2015-01-05
Thx, Here u are.

```
lsusb
```
```
Bus 002 Device 003: ID 2232:1035  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 192f:0416 Avago Technologies, Pte. ADNS-5700 Optical Mouse Controller (3-button)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
dmesg | grep firmware
```
```
[    2.457440] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f00)
```
```
uname -a
```
```
Linux savabox 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by jeremy31 on 2015-01-05
So what modules are loaded```
lsmod | grep bluetooth
```

---

### Post by dentaku65 on 2015-01-05
The module loaded:
> bluetooth             391136  23 bnep,ath3k,btusb,rfcomm

---

### Post by jeremy31 on 2015-01-05
Everything looks good, with another bluetooth device in discovery mode```
hcitool scan
```

---

### Post by dentaku65 on 2015-01-06
Hi,

seems solved, I'm able to see the bluetooth devices of my neighbors but not my owns :mad:

Anyway I mark the tread as solved

---

