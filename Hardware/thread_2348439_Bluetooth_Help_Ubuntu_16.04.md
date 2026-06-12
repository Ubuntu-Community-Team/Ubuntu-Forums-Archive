---
title: "Bluetooth Help Ubuntu 16.04"
date: 2017-01-03
forum: Hardware
---

### Post by johnnyt2 on 2017-01-03
Hi everyone....

I installed Ubuntu the other day and everything has went fairly smoothly expect i haven't been able to get my computers Bluetooth to work. I'v been trying to read random post on google that are similar to my problem but i haven't been able to solve...
When i try to turn it on in settings nothing shows up, i'm 100% sure that i have bluetooth on my computer since i had it when i had windows installed. I'm not sure what the problem is and how to approach the problem. However it is possible that i don't have the needed drivers installed seeing as i also had to manually install wifi drivers. I would appreciate any help with this problem since i do not really know what im doing in Ubuntu and have no idea how to fix this.

[IMG]http://i63.tinypic.com/qqbsjk.png[/IMG]
 

john@X555LAB:~$ hciconfig -a
```
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 70:77:81:5B:03:00  ACL MTU: 1021:4  SCO MTU: 128:2
    DOWN 
    RX bytes:1160 acl:0 sco:0 events:62 errors:0
    TX bytes:742 acl:0 sco:0 commands:62 errors:0
    Features: 0xff 0xff 0x8f 0xfe 0xdb 0xff 0x5b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 

```
john@X555LAB:~$ sudo service bluetooth status
```
[sudo] password for john: 
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: active (running) since Tue 2017-01-03 12:17:50 EST; 6h ago
     Docs: man:bluetoothd(8)
 Main PID: 927 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;927 /usr/lib/bluetooth/bluetoothd


Jan 03 12:17:50 X555LAB systemd[1]: Starting Bluetooth service...
Jan 03 12:17:50 X555LAB bluetoothd[927]: Bluetooth daemon 5.37
Jan 03 12:17:50 X555LAB systemd[1]: Started Bluetooth service.
Jan 03 12:17:50 X555LAB bluetoothd[927]: Starting SDP server
Jan 03 12:17:50 X555LAB bluetoothd[927]: Bluetooth management interface 1.10 ini

```

john@X555LAB:~$ hcitool dev 
```
Devices:

```


Any Input is appreciated 

Thanks

---

### Post by jeremy31 on 2017-01-03
Please post results from terminal for ```
lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'
```

---

### Post by johnnyt2 on 2017-01-03
john@X555LAB:~$ lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
	Kernel driver in use: r8169
	Kernel modules: r8169
03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
	Subsystem: Foxconn International, Inc. MT7630e 802.11bgn Wireless Network Adapter [105b:e084]
	Kernel driver in use: mt7630e
	Kernel modules: mt7630e
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 0e8d:763f MediaTek Inc. 
Bus 001 Device 004: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 045e:07b2 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
[    1.467755] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x381f00)
[   14.214163] Bluetooth: Core ver 2.21
[   14.214176] Bluetooth: HCI device and connection manager initialized
[   14.214178] Bluetooth: HCI socket layer initialized
[   14.214180] Bluetooth: L2CAP socket layer initialized
[   14.214183] Bluetooth: SCO socket layer initialized
[   28.914178] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.914180] Bluetooth: BNEP filters: protocol multicast
[   28.914184] Bluetooth: BNEP socket layer initialized
[   31.391481] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'MT7650E234.bin'
[   31.600129] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 112.3
[   31.614175] rt2800_load_firmware: COM_REG0(0x730) = 0x1

```

---

### Post by jeremy31 on 2017-01-03
Unfortunately I have no idea how to make that bluetooth device work and I would suggest filing a bug report, see [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078) and file the bug report against package linux or bluez

---

### Post by johnnyt2 on 2017-01-03
Ok Thanks ill do that 

i noticed that you ran 
```
[COLOR=#000000]rfkill list all;[/COLOR]
```
Their was originally a soft block but i removed it not really sure if that matters....

I don't know what the majority of the output code means for must of the commands i run... is there a way to check if i have the correct drivers installed ?

---

### Post by johnnyt2 on 2017-01-03
I fixed it now btw thanks for your help

I had forgotten to run a batch file when installing my wifi driver i guess it patched the blue tooth...

---

