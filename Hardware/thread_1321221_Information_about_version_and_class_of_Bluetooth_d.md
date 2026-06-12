---
title: "Information about version and class of Bluetooth dongle"
date: 2009-11-09
forum: Hardware
---

### Post by FunKing on 2009-11-09
Hello, world!

I just bought a Blutetooth adapter (which looks just like any small BT USB dongle). Since it has no external marks to identify it, how can I know it is the correct BT version and class that I wanted?

This is the only information that I could get from it:

```
ric@ubuntu-p4:~$ hciconfig -a
hci0:    Type: USB
    BD Address: 00:15:83:15:A3:10 ACL MTU: 672:4 SCO MTU: 48:1
    UP RUNNING PSCAN 
    RX bytes:703 acl:0 sco:0 events:24 errors:0
    TX bytes:103 acl:0 sco:0 commands:24 errors:0
    Features: 0xff 0x3e 0x85 0x38 0x18 0x18 0x00 0x00
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: ''
    Class: 0x4a0100
    Service Classes: Networking, Capturing, Telephony
    Device Class: Computer, Uncategorized
    HCI Ver: 2.0 (0x3) HCI Rev: 0xc5c LMP Ver: 2.0 (0x3) LMP Subver: 0xc5c
    Manufacturer: Cambridge Silicon Radio (10)
```Any tip would be appreciated.

Thank you!

---

