---
title: "Bluetooth cant seek devices"
date: 2019-01-05
forum: Hardware
---

### Post by BeauteousBlooms on 2019-01-05
So just to put it out there, i have ran {[COLOR=#000000][FONT=&quot]lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'}[/FONT][/COLOR]   and the output were as follows:

01:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
	Kernel driver in use: wl
Bus 002 Device 002: ID 2357:0601  
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 001 Device 005: ID 0a5c:216d Broadcom Corp. 
Bus 001 Device 003: ID 04f2:b544 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 04d9:a070 Holtek Semiconductor, Inc. 
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:	Type: Primary  Bus: USB
	BD Address: 60:6D:C7:F0:0F:1E  ACL MTU: 1021:8  SCO MTU: 64:1
	UP RUNNING PSCAN ISCAN 
	RX bytes:3113 acl:12 sco:0 events:182 errors:0
	TX bytes:13347 acl:15 sco:0 commands:149 errors:0
	Features: 0xff 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF 
	Link mode: SLAVE ACCEPT 
	Name: 'rom-HP-ENVY-Notebook'
	Class: 0x1c010c
	Service Classes: Rendering, Capturing, Object Transfer
	Device Class: Computer, Laptop
	HCI Version: 4.0 (0x6)  Revision: 0x149
	LMP Version: 4.0 (0x6)  Subversion: 0x210b
	Manufacturer: Broadcom Corporation (15)


[    0.028000] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.057289] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.631301] [drm] Finished loading DMC firmware i915/skl_dmc_ver1_26.bin (v1.26)
[    5.230317] Bluetooth: Core ver 2.22
[    5.230331] Bluetooth: HCI device and connection manager initialized
[    5.230334] Bluetooth: HCI socket layer initialized
[    5.230336] Bluetooth: L2CAP socket layer initialized
[    5.230341] Bluetooth: SCO socket layer initialized
[    5.362219] Bluetooth: hci0: BCM: chip id 70
[    5.363213] Bluetooth: hci0: BCM: features 0x06
[    5.379230] Bluetooth: hci0: DESKTOP-P2S4AMS
[    5.379233] Bluetooth: hci0: BCM (001.001.011) build 0329
[    5.386023] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[    5.386026] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[    7.200488] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.200490] Bluetooth: BNEP filters: protocol multicast
[    7.200494] Bluetooth: BNEP socket layer initialized
[   16.966006] Bluetooth: RFCOMM TTY layer initialized
[   16.966013] Bluetooth: RFCOMM socket layer initialized
[   16.966019] Bluetooth: RFCOMM ver 1.11
[26658.274447] Bluetooth: hci0: last event is not cmd complete (0x0f)
[26669.282275] Bluetooth: hci0: last event is not cmd complete (0x0f)


I'm no terminal god so this really doesnt mean anything to me, so could somebody tell me what is going on, that would be great. thanks in advance. (also i think is the problem is :[    5.386023] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2. But again what do i know.....)

---

### Post by clementc on 2019-01-05
Hi [**[COLOR=#000000]BeauteousBlooms[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115487"),

This Git repository might be of help to you:

[https://github.com/winterheart/broadcom-bt-firmware](https://github.com/winterheart/broadcom-bt-firmware)

You will have to download the correct firmware from the brcm folder (.hcd file), rename it to BCM.hcd, then place it into the following folder:

/lib/firmware/brcm

You will notice that there are multiple firmwares for the same adapter model (BCM43142A0-*.hcd), you will need to find out which one to use.

---

### Post by BeauteousBlooms on 2019-01-11
I post has been made about this before, but instead or replying i just thought to rewrite it again. i have pulse-audio and blueman installed, as well as the blue tooth module for pulse audio. With all these software, bluetooth devices still cannot be found (e.g my bose sound link), on very rare occasions it can find it and successfully connect to it, but upon next attempt to connect it fails and the cycle continues. In my previous post i was given a github link ([https://github.com/winterheart/broadcom-bt-firmware](https://github.com/winterheart/broadcom-bt-firmware)), follow it to find my driver and place it in /brcm. I highly doubt the driver is the problem since it does occasionally work, ( about 1/10 tries), so this inconstancy is what is annoying. if anyone knows anything and can help me, that will be greatly appreciated.  


**output of **[COLOR=#000000][B]lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm' :
[/B]
[/COLOR][COLOR=#000000]1:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)[/COLOR]
[COLOR=#000000]Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a][/COLOR]
[COLOR=#000000]Kernel driver in use: wl[/COLOR]
[COLOR=#000000]Bus 002 Device 002: ID 2357:0601 [/COLOR]
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/COLOR]
[COLOR=#000000]Bus 001 Device 006: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor[/COLOR]
[COLOR=#000000]Bus 001 Device 005: ID 0a5c:216d Broadcom Corp. [/COLOR]
[COLOR=#000000]Bus 001 Device 003: ID 04f2:b544 Chicony Electronics Co., Ltd [/COLOR]
[COLOR=#000000]Bus 001 Device 004: ID 04d9:a070 Holtek Semiconductor, Inc. [/COLOR]
[COLOR=#000000]Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. Hub[/COLOR]
[COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]hci0:	Type: Primary Bus: USB[/COLOR]
[COLOR=#000000]BD Address: 60:6D:C7:F0:0F:1E ACL MTU: 1021:8 SCO MTU: 64:1[/COLOR]
[COLOR=#000000]UP RUNNING PSCAN ISCAN [/COLOR]
[COLOR=#000000]RX bytes:3113 acl:12 sco:0 events:182 errors:0[/COLOR]
[COLOR=#000000]TX bytes:13347 acl:15 sco:0 commands:149 errors:0[/COLOR]
[COLOR=#000000]Features: 0xff 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87[/COLOR]
[COLOR=#000000]Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 [/COLOR]
[COLOR=#000000]Link policy: RSWITCH HOLD SNIFF [/COLOR]
[COLOR=#000000]Link mode: SLAVE ACCEPT [/COLOR]
[COLOR=#000000]Name: 'rom-HP-ENVY-Notebook'[/COLOR]
[COLOR=#000000]Class: 0x1c010c[/COLOR]
[COLOR=#000000]Service Classes: Rendering, Capturing, Object Transfer[/COLOR]
[COLOR=#000000]Device Class: Computer, Laptop[/COLOR]
[COLOR=#000000]HCI Version: 4.0 (0x6) Revision: 0x149[/COLOR]
[COLOR=#000000]LMP Version: 4.0 (0x6) Subversion: 0x210b[/COLOR]
[COLOR=#000000]Manufacturer: Broadcom Corporation (15)[/COLOR]


[COLOR=#000000][ 0.028000] Spectre V2 : Enabling Restricted Speculation for firmware calls[/COLOR]
[COLOR=#000000][ 0.057289] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored[/COLOR]
[COLOR=#000000][ 1.631301] [drm] Finished loading DMC firmware i915/skl_dmc_ver1_26.bin (v1.26)[/COLOR]
[COLOR=#000000][ 5.230317] Bluetooth: Core ver 2.22[/COLOR]
[COLOR=#000000][ 5.230331] Bluetooth: HCI device and connection manager initialized[/COLOR]
[COLOR=#000000][ 5.230334] Bluetooth: HCI socket layer initialized[/COLOR]
[COLOR=#000000][ 5.230336] Bluetooth: L2CAP socket layer initialized[/COLOR]
[COLOR=#000000][ 5.230341] Bluetooth: SCO socket layer initialized[/COLOR]
[COLOR=#000000][ 5.362219] Bluetooth: hci0: BCM: chip id 70[/COLOR]
[COLOR=#000000][ 5.363213] Bluetooth: hci0: BCM: features 0x06[/COLOR]
[COLOR=#000000][ 5.379230] Bluetooth: hci0: DESKTOP-P2S4AMS[/COLOR]
[COLOR=#000000][ 5.379233] Bluetooth: hci0: BCM (001.001.011) build 0329[/COLOR]
[COLOR=#000000][ 5.386023] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2[/COLOR]
[COLOR=#000000][ 5.386026] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found[/COLOR]
[COLOR=#000000][ 7.200488] Bluetooth: BNEP (Ethernet Emulation) ver 1.3[/COLOR]
[COLOR=#000000][ 7.200490] Bluetooth: BNEP filters: protocol multicast[/COLOR]
[COLOR=#000000][ 7.200494] Bluetooth: BNEP socket layer initialized[/COLOR]
[COLOR=#000000][ 16.966006] Bluetooth: RFCOMM TTY layer initialized[/COLOR]
[COLOR=#000000][ 16.966013] Bluetooth: RFCOMM socket layer initialized[/COLOR]
[COLOR=#000000][ 16.966019] Bluetooth: RFCOMM ver 1.11[/COLOR]
[COLOR=#000000][26658.274447] Bluetooth: hci0: last event is not cmd complete (0x0f)[/COLOR]
[COLOR=#000000][26669.282275] Bluetooth: hci0: last event is not cmd complete (0x0f)[/COLOR]

---

### Post by oldos2er on 2019-01-11
Threads merged. Please don't create duplicate threads, it's confusing and it dilutes the community's ability to help.

---

