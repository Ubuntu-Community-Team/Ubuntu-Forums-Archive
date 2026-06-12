---
title: "bluetooth not working"
date: 2011-11-22
forum: Hardware
---

### Post by snowguy on 2011-11-22
I used to see the bluetooth icon at the top right of the screen but when I would scan it would never pick up anything. I don't think it is a hardware problem because I could use bluetooth fine when I boot into windows.

The funny thing was that though I could see the bluetooth icon in ubuntu and I saw bluetooth under rfkill list and lsusb, no devices were listed for hcitool dev. I wasn't sure where to go from there. 

I saw on another thread that someone's 11.10 bluetooth problems were fixed when they reinstalled bluetooth stuff. so I loaded up synaptic and filtered on all installed packages with "blue" marked them all for re-installation and then restarted. Now bluetooth icon no longer shows up at all. I also noticed that bluetooth dropped out of rfkill list and lsusb (before they showed up there.)

any suggestions on where to go from here?

Here are some commands for troubleshooting that I picked up from other bluetooth threads:

```

dmesg |grep -i bluetooth
[    5.102895] Bluetooth: Core ver 2.16
[    5.102913] Bluetooth: HCI device and connection manager initialized
[    5.102915] Bluetooth: HCI socket layer initialized
[    5.102917] Bluetooth: L2CAP socket layer initialized
[    5.102952] Bluetooth: SCO socket layer initialized
[    5.105978] Bluetooth: RFCOMM TTY layer initialized
[    5.105987] Bluetooth: RFCOMM socket layer initialized
[    5.105989] Bluetooth: RFCOMM ver 1.11
[    5.124877] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.124880] Bluetooth: BNEP filters: protocol multicast

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 05ca:181e Ricoh Co., Ltd 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver

sudo hcitool dev 
Devices:

sudo rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Before I reinstalled all the "blue" modules here is what the same commands gave me--which I assume if I am really desperate I could get by reinstalling ubuntu from scratch.
```

dmesg |grep -i bluetooth
[    4.473211] Bluetooth: Core ver 2.16
[    4.474054] Bluetooth: HCI device and connection manager initialized
[    4.474056] Bluetooth: HCI socket layer initialized
[    4.474058] Bluetooth: L2CAP socket layer initialized
[    4.475050] Bluetooth: SCO socket layer initialized
[    4.485033] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    4.966908] Bluetooth: RFCOMM TTY layer initialized
[    4.966913] Bluetooth: RFCOMM socket layer initialized
[    4.966915] Bluetooth: RFCOMM ver 1.11
[    4.968914] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.968916] Bluetooth: BNEP filters: protocol multicast

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 05ca:181e Ricoh Co., Ltd 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module


sudo hcitool dev
Devices: 


sudo rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---

### Post by snowguy on 2012-02-15
I just happened to try again today and it all works. I assume some update came through in the last while that fixed it. 

FYI, once you connect the bluetooth you need to go to sound (search for it) and then click on the output tab and select the output device you want.

---

