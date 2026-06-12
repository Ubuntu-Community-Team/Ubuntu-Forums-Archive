---
title: "1000H with Maverick runs Bluetooth 2.1 ???"
date: 2011-01-23
forum: Hardware
---

### Post by weeix on 2011-01-23
I'm using Ubuntu 10.10 with my old 1000H and have a problem with the Bluetooth device. -- When I try to send a file from my laptop to my cellphone, it performs like this

[IMG]http://img710.imageshack.us/img710/6368/trytoconnect.png[/IMG]

and then (Please note that 1. there aren't any physical address after 'From:' 2. address of the cellphone in Fig.1 and Fig.2 doesn't match)

[IMG]http://img443.imageshack.us/img443/114/bluetootherror.png[/IMG]

(lsusb)
```
Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
```(hciconfig -a hci0)
```
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:15:AF:F8:C3:2C  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:5592 acl:42 sco:0 events:163 errors:0
    TX bytes:3522 acl:40 sco:0 commands:99 errors:0
    Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x83
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'WeeIX-1000H'
    Class: 0x480100
    Service Classes: Capturing, Telephony
    Device Class: Computer, Uncategorized
    HCI Version: 2.1 (0x4)  Revision: 0x50f1
    LMP Version: 2.1 (0x4)  Subversion: 0x420e
    Manufacturer: Broadcom Corporation (15)

```And why is my 1000H using Bluetooth 2.1, doesn't it suppose to use Broadcom 2045 Bluetooth 2.0 ?

---

### Post by weeix on 2011-01-23
Bump @ 24/01/11

---

### Post by weeix on 2011-01-24
Bump @ 25/01/11

---

### Post by weeix on 2011-01-25
Bump @ 26/01/11

---

### Post by weeix on 2011-01-26
Bump @ 27/01/11

---

### Post by rocthrttle on 2011-01-26
can you do it with a cable? that might just be the way to do it. otherwise i'm stumped. sorry. i got nothing.

---

### Post by weeix on 2011-01-27
^
I could transfer files via micro sd card, but that would be inconvenient.
And I think a good OS should be able to use every hardwares properly, especially built-in hardwares.

---

### Post by NightwishFan on 2011-01-27
Yes, sure, who is going to write the drivers for this good os? Not every manufacturer is Linux friendly.

---

### Post by weeix on 2011-01-28
[COLOR=Silver]^ I think it's not about the manufacturer, because this device used to work properly in the old linux kernel.

[COLOR=Black]My bad. I forgot, previously, I use another method -- click the bluetooth applet icon and then "Send files to device...". *(This method works until now)*
But this time, I click the bluetooth applet icon, select my cellphone and then "Send files...[COLOR=Silver][COLOR=Black]", so I'm unable to send any file.


[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by weeix on 2011-01-28
I see. So this an issue with the manufacturer and can't be solved.

I'll stop bumping then.

Thanks for spending your time reading / replying.

---

### Post by NightwishFan on 2011-01-28
Not necessarily, I was just pointing that out. If it worked previously file a bug about it and mention it as a regression.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

