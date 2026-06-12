---
title: "[Bluetooth] Accel-OB1 - Cannot pair/connect with any device!"
date: 2010-10-10
forum: Hardware
---

### Post by White-Energy on 2010-10-10
Well here's the story, yesterday i just moved to ubuntu 10.10 and as i've been using bluetooth headset (Calypso-BT from Media-Tech) i thought maybe they'll work on ubuntu... when i'm trying to connect/pair any device though the bluetooth it says "Failed" or "Error" i've been searching on google a solution but couldn't find any.. here's my setup:
```
$ hciconfig -a hci0
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:1F:81:00:00:01  ACL MTU: 339:6  SCO MTU: 180:1
	UP RUNNING PSCAN 
	RX bytes:5117 acl:1 sco:0 events:389 errors:0
	TX bytes:2269 acl:1 sco:0 commands:364 errors:1
	Features: 0xef 0x3e 0x09 0xf0 0x0b 0x08 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'Accel-OB1'
	Class: 0x480100
	Service Classes: Capturing, Telephony
	Device Class: Computer, Uncategorized
	HCI Version: 1.2 (0x2)  Revision: 0x2
	LMP Version: 1.2 (0x2)  Subversion: 0x2
	Manufacturer: Accel Semiconductor Ltd. (74)


```

Can't find any solution, please! help.. i'm a human just like you!

---

### Post by White-Energy on 2010-10-18
Anyone? :(

---

### Post by mmtrt on 2011-02-03
I have same BT device with same problem with it and tried various methods but non of them worked. Well it discovers the devices but it is not pairing or sending files to device failed to work and my bt device is working in xp and win7 fine...

hciconf of BT
```
:~$ hciconfig -a output
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:1F:81:00:00:01  ACL MTU: 339:6  SCO MTU: 180:1
	UP RUNNING PSCAN ISCAN 
	RX bytes:7434 acl:0 sco:0 events:216 errors:0
	TX bytes:2171 acl:0 sco:0 commands:183 errors:0
	Features: 0xef 0x3e 0x09 0xf0 0x0b 0x08 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'bt-dev'
	Class: 0x480100
	Service Classes: Capturing, Telephony
	Device Class: Computer, Uncategorized
	HCI Version: 1.2 (0x2)  Revision: 0x2
	LMP Version: 1.2 (0x2)  Subversion: 0x2
	Manufacturer: Accel Semiconductor Ltd. (74)

```
using ubuntu 10.10 up2date...

Any Fix or Help needed.

---

### Post by zwayon on 2011-03-02
i also got this problem, my OS can discover my phone, but it neither pair nor connect. anyone help? :???:

---

