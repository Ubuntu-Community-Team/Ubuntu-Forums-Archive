---
title: "Intel NUC 10 not seeing Bluetooth LE clients"
date: 2022-04-16
forum: Hardware
---

### Post by scurvydog33 on 2022-04-16
I have an Intel NUC10 running Ubuntu 20.04 and having issue with bluetooth LE clients (Ruuvi tag) connecting. The Ruuvi tags use BLE connections and are working fine as I can see them with my iPhone and Mac. On my NUC I cannot connect to a classic bluetooth device like my phone using bluetoothctl so I know that component is working. Research shows that if I go into bluetoothctl (v5.53) and go into the scan menu and set transport le and then scan on I should see the Ruuvi tags show up. I ran btmon on the same time and did not see and messages from the tags. 

One area of concern is that the system is identifying the incorrect wireless chip for bluetooth. The NUC has the AX201 installed on the board. See output below

dmesg shows AX201 wireless chipset which matches the data sheet
*"iwlwifi 0000:00:14.3: Detected **Intel(R) Wi-Fi 6 AX201** 160MHz, REV=0x354"*

However lshw commands shows
network:0 DISABLED
             description: Wireless interface
**             product: Wireless-AC 9462**
             vendor: Intel Corporation

Further Detail:
hciconfig -a
hci0:    Type: Primary  Bus: USB
    BD Address: 98:AF:65:A1:D8:CA  ACL MTU: 1021:4  SCO MTU: 96:6
    UP RUNNING PSCAN 
    RX bytes:14539 acl:100 sco:0 events:1581 errors:0
    TX bytes:19494 acl:100 sco:0 commands:1457 errors:0
    Features: 0xbf 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'voyager'
    Class: 0x0c0104
    Service Classes: Rendering, Capturing
    Device Class: Computer, Desktop workstation
    HCI Version: 5.1 (0xa)  Revision: 0x100
    LMP Version: 5.1 (0xa)  Subversion: 0x100
    Manufacturer: Intel Corp. (2)

---

### Post by him610 on 2022-04-18
The term *Ruuvi tags* is/was unfamiliar to me, so I looked up...
RE: [https://ruuvi.com/ruuvitag/?gclid=Cj0KCQjwmPSSBhCNARIsAH3cYgaSB1TBnzFacdXvPAY1B45n4gxQqiYA3jr80dOeRp4ZLA_Kpq9EGnwaAgqyEALw_wcB]("https://ruuvi.com/ruuvitag/?gclid=Cj0KCQjwmPSSBhCNARIsAH3cYgaSB1TBnzFacdXvPAY1B45n4gxQqiYA3jr80dOeRp4ZLA_Kpq9EGnwaAgqyEALw_wcB")
> RuuviTag is a wireless Bluetooth sensor node that measures temperature, air humidity, air pressure and movement. You can read live measurements and history data directly on your smartphone using Ruuvi’s mobile app for Android and iOS
Please note on the last line,  *...for Android and iOS*
Unless I missed it, there is no reference to its being available to Linux machines.

---

### Post by #&amp;thj^% on 2022-04-18
Might be worth a look on a PI/4
[https://github.com/ttu/ruuvitag-sensor](https://github.com/ttu/ruuvitag-sensor)
forum: [https://f.ruuvi.com/t/debian-linux-and-ruuvitag-where-to-start/180](https://f.ruuvi.com/t/debian-linux-and-ruuvitag-where-to-start/180)

---

