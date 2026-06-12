---
title: "Bluetooth mouse not detected/connecting after recharge"
date: 2020-09-28
forum: Hardware
---

### Post by makem2 on 2020-09-28
I am using a Dell XPS13 9300 laptop with an unbranded Bluetooth mouse. When the mouse has charge and I start the laptop the mouse is connected and working correctly.

If whilst using the mouse it needs recharging, I use the touch pad whilst the mouse is being charged.

After a full charge I am unable to use the mouse. It does not connect even if I set it up again.

If I restart the laptop the mouse will work again until it needs another charge.

I should not need to restart the machine every time I charge the mouse.

The machine is dual boot with windows and Dell provide the same machine with Ubuntu installed. The mouse does not have this problem with Windows.

```

makem@XPS-13-9300:~$ hciconfig -a
hci0:	Type: Primary  Bus: USB
	BD Address: 04:33:C2:19:FC:89  ACL MTU: 1021:4  SCO MTU: 96:6
	UP RUNNING PSCAN ISCAN 
	RX bytes:37502 acl:2575 sco:0 events:111 errors:0
	TX bytes:7650 acl:9 sco:0 commands:92 errors:0
	Features: 0xbf 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH SNIFF 
	Link mode: SLAVE ACCEPT 
	Name: 'XPS-13-9300'
	Class: 0x1c010c
	Service Classes: Rendering, Capturing, Object Transfer
	Device Class: Computer, Laptop
	HCI Version: 5.1 (0xa)  Revision: 0x100
	LMP Version: 5.1 (0xa)  Subversion: 0x100
	Manufacturer: Intel Corp. (2)


makem@XPS-13-9300:~$ cat /etc/issue*
Ubuntu 20.04.1 LTS \n \l


Ubuntu 20.04.1 LTS
makem@XPS-13-9300:~$ 



```

---

