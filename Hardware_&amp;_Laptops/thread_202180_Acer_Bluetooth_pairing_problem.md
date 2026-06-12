---
title: "Acer Bluetooth pairing problem"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by hartogvdb on 2006-06-23
I have an Acer Ferrari with built in bluetooth that doesn't want to know about pairing my headset. 
Does anybody understand what is missing. My friend has many more features on his Dell. And does not have any pairing problems.
Is there any documentation of what these features do or represent?

It shows the following details:
hartog@ferrari:~$ sudo hciconfig hci0 revision
hci0: Type: USB
BD Address: 00:0B:6B:91:50:62 ACL MTU: 377:10 SCO MTU: 64:8
Firmware 105.105 / 74
hartog@ferrari:~$ sudo hciconfig hci0 features
hci0: Type: USB
BD Address: 00:0B:6B:91:50:62 ACL MTU: 377:10 SCO MTU: 64:8
Features: 0xff 0xff 0x0d 0x38 0x08 0x08 0x00 0x00
<3-slot packets> <5-slot packets> <encryption> <slot offset>
<timing accuracy> <role switch> <hold mode> <sniff mode>
<park state> <RSSI> <channel quality> <SCO link> <HV2 packets>
<HV3 packets> <u-law log> <A-law log> <CVSD> <power control>
<transparent SCO> <enhanced iscan> <interlaced iscan>
<interlaced pscan> <AFH cap. slave> <AFH cap. master>
hartog@ferrari:~$ sudo hciconfig hci0 version
hci0: Type: USB
BD Address: 00:0B:6B:91:50:62 ACL MTU: 377:10 SCO MTU: 64:8
HCI Ver: 1.2 (0x2) HCI Rev: 0x69 LMP Ver: 1.2 (0x2) LMP Subver: 0x694a
Manufacturer: Broadcom Corporation (15)

---

