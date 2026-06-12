---
title: "Bluetooth suddenly stopped working, device not detected"
date: 2013-08-09
forum: Hardware
---

### Post by elang on 2013-08-09
I use Ubuntu 12.04 32b on a Dell Insipiron N5010. It has a Dell Bluetooth 365 adapter.

It **was working great** until a few days ago, and is now giving me problems.


[LIST=1]
[*]The bluetooth icon is still visible in the top bar, and it says _**Bluetooth: On**_ and shows me a working option to turn it off. Turning it off and then on again does not help 
[*]Bluetooth Settings: The slider to power on Bluetooth keeps reverting to off even when I drag it to on
[ATTACH=CONFIG]245230[/ATTACH] 
[*]Command line outputs
[LIST]
[*]lsusb
```

elan@b4tc4v3:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0c45:641d Microdia 1.3 MPixel Integrated Webcam
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 004: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 005: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]

``` 
[*]rfkill list
```

elan@b4tc4v3:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``` 
[*]hcitool dev
```

elan@b4tc4v3:~$ hcitool dev
Devices:

``` 
[*]hciconfig -a **(shows no output)**
```

elan@b4tc4v3:~$ hciconfig-a
elan@b4tc4v3:~$ 

``` 
[/LIST]
   
[/LIST]

I am unable to use Bluetooth at all, please help

---

### Post by David_Semeria on 2013-08-11
I have exactly the problem (Dell Precision laptop).
Everything working like a dream until I rebooted after a system update.
Something has clearly changed.
I managed to track the problem down to a dbus error message:

> org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken

But that's as far as I got.
Any help by Bluetooth gurus would be greatly appreciated

---

### Post by David_Semeria on 2013-08-11
I have exactly the problem (Dell Precision laptop).
Everything working like a dream until I rebooted after a system update.
Something has clearly changed.
I managed to track the problem down to a dbus error message:

> org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken

But that's as far as I got.
Any help by Bluetooth gurus would be greatly appreciated

EDIT.

I spotted the following lines in the syslog that don't look too encouraging...

> Aug 11 15:26:36 vlap2 bluetoothd[654]: Discovery session 0x7f78597bc170 with :1.60 activated
Aug 11 15:26:39 vlap2 bluetoothd[654]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/HFPAG
Aug 11 15:26:39 vlap2 bluetoothd[654]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/A2DPSource
Aug 11 15:26:39 vlap2 bluetoothd[654]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/A2DPSink

---

### Post by varunendra on 2013-08-11
> **elang said:**
> 
1. The bluetooth icon is still visible in the top bar, and it says _**Bluetooth: On**_ and shows me a working option to turn it off. Turning it off and then on again does not help
2. Bluetooth Settings: The slider to power on Bluetooth keeps reverting to off even when I drag it to on
[ATTACH=CONFIG]245230[/ATTACH]


Exactly the same behaviour I get with my internal BT adapter. I have created a script to reset the internal USB hub on which the adapter is located, works perfectly for me.

Please take a look at post #7 in this thread [http://ubuntuforums.org/showthread.php?t=2142366](http://ubuntuforums.org/showthread.php?t=2142366)

You will most probably need to change the bus/device IDs to match yours. If it works, we can create a script for you to reset the hub/adapter when required.

@ David_Semeria,
Same recommendation for you too. Try the commands (with IDs modified to match your case) temporarily. If they seem to work reliably, you can convert them to a convenient script.

---

### Post by David_Semeria on 2013-08-11
Thanks @Varun
My problem is slightly different.
The BT adapter appears to be working fine. It can discover devices without issue. The problem is during pairing. As can be seen from the following output

Manual pairing
> 
# hcitool scan
Scanning ...
    7C:1E:52:6A:72:50    Microsoft Sculpt Touch Mouse
# bluez-simple-agent hci0 7C:1E:52:6A:72:50
Release
Creating device failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


hcidump:
> HCI sniffer - Bluetooth packet analyzer ver 2.2device: hci0 snap_len: 1028 filter: 0xffffffffffffffff
< HCI Command: Inquiry (0x01|0x0001) plen 5
    lap 0x9e8b33 len 8 num 0
> HCI Event: Command Status (0x0f) plen 4
    Inquiry (0x01|0x0001) status 0x00 ncmd 1
> HCI Event: Inquiry Result with RSSI (0x22) plen 15
    bdaddr 7C:1E:52:6A:72:50 mode 1 clkoffset 0x1b38 class 0x002580 rssi -69
> HCI Event: Inquiry Complete (0x01) plen 1
    status 0x00
< HCI Command: Create Connection (0x01|0x0005) plen 13
    bdaddr 7C:1E:52:6A:72:50 ptype 0xcc18 rswitch 0x01 clkoffset 0x0000
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 
> HCI Event: Command Status (0x0f) plen 4
    Create Connection (0x01|0x0005) status 0x00 ncmd 1
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 11 bdaddr 7C:1E:52:6A:72:50 type ACL encrypt 0x00
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
    handle 11
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 11
    Features: 0xbc 0x06 0x86 0x78 0x18 0x1c 0x59 0x87
< HCI Command: Read Remote Extended Features (0x01|0x001c) plen 3
    handle 11 page 1
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Extended Features (0x01|0x001c) status 0x00 ncmd 1
> HCI Event: Read Remote Extended Features (0x23) plen 13
    status 0x00 handle 11 page 1 max 1
    Features: 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
    bdaddr 7C:1E:52:6A:72:50 mode 2 clkoffset 0x0000
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 7C:1E:52:6A:72:50 name 'Microsoft Sculpt Touch Mouse'
< HCI Command: Authentication Requested (0x01|0x0011) plen 2
    handle 11
> HCI Event: Command Status (0x0f) plen 4
    Authentication Requested (0x01|0x0011) status 0x00 ncmd 1
> HCI Event: Link Key Request (0x17) plen 6
    bdaddr 7C:1E:52:6A:72:50
< HCI Command: Link Key Request Negative Reply (0x01|0x000c) plen 6
    bdaddr 7C:1E:52:6A:72:50
> HCI Event: Command Complete (0x0e) plen 10
    Link Key Request Negative Reply (0x01|0x000c) ncmd 1
    status 0x00 bdaddr 7C:1E:52:6A:72:50
> HCI Event: IO Capability Request (0x31) plen 6
    bdaddr 7C:1E:52:6A:72:50
< HCI Command: IO Capability Request Reply (0x01|0x002b) plen 9
    bdaddr 7C:1E:52:6A:72:50 capability 0x01 oob 0x00 auth 0x03
    Capability: DisplayYesNo (OOB data not present)
    Authentication: Dedicated Bonding (MITM Protection)
> HCI Event: Command Complete (0x0e) plen 10
    IO Capability Request Reply (0x01|0x002b) ncmd 1
    status 0x00 bdaddr 7C:1E:52:6A:72:50
> HCI Event: IO Capability Response (0x32) plen 9
    bdaddr 7C:1E:52:6A:72:50 capability 0x03 oob 0x00 auth 0x04
    Capability: NoInputNoOutput (OOB data not present)
    Authentication: General Bonding (No MITM Protection)
> HCI Event: User Confirmation Request (0x33) plen 10
    bdaddr 7C:1E:52:6A:72:50 passkey 920357
< HCI Command: User Confirmation Request Reply (0x01|0x002c) plen 6
    bdaddr 7C:1E:52:6A:72:50
> HCI Event: Command Complete (0x0e) plen 10
    User Confirmation Request Reply (0x01|0x002c) ncmd 1
    status 0x00 bdaddr 7C:1E:52:6A:72:50
> HCI Event: Simple Pairing Complete (0x36) plen 7
    status 0x00 bdaddr 7C:1E:52:6A:72:50
> HCI Event: Link Key Notification (0x18) plen 23
    bdaddr 7C:1E:52:6A:72:50 key B0D25550FDF274E6BD88261FF527C7B3 type 4
    Type: Unauthenticated Combination Key
> HCI Event: Auth Complete (0x06) plen 3
    status 0x00 handle 11
< HCI Command: Set Connection Encryption (0x01|0x0013) plen 3
    handle 11 encrypt 0x01
> HCI Event: Command Status (0x0f) plen 4
    Set Connection Encryption (0x01|0x0013) status 0x00 ncmd 1
> HCI Event: Encrypt Change (0x08) plen 4
    status 0x00 handle 11 encrypt 0x01
< ACL data: handle 11 flags 0x00 dlen 10
    L2CAP(s): Info req: type 2
< ACL data: handle 11 flags 0x00 dlen 12
    L2CAP(s): Connect req: psm 1 scid 0x0040
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 1 packets 1
< HCI Command: Disconnect (0x01|0x0006) plen 3
    handle 11 reason 0x13
    Reason: Remote User Terminated Connection
> HCI Event: Command Status (0x0f) plen 4
    Disconnect (0x01|0x0006) status 0x00 ncmd 1
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 11 reason 0x16
    Reason: Connection Terminated by Local Host
< HCI Command: Delete Stored Link Key (0x03|0x0012) plen 7
    bdaddr 7C:1E:52:6A:72:50 all 0
> HCI Event: Command Complete (0x0e) plen 6
    Delete Stored Link Key (0x03|0x0012) ncmd 1
    status 0x00 deleted 0


The device appears to be either hanging up before the pairing completes, or it is sending a response which is not finding its way back to the controller...

The really annoying thing is that both the BT keyboard and mouse were working perfectly until the upgrade....

---

### Post by varunendra on 2013-08-11
David_Semeria,

I have no experience with that kind of problem, and am currently too short of time to dig deeper into it. So I'm sorry, can't help with it right now.

I Hope and wish someone else with more ideas could see the post and join us with their suggestions.

---

### Post by babeliak on 2014-06-19
I have similar problem, my BlueTooth stopped working (I use BT mouse) and Ubuntu now disconnects all my devices:
```
georg@ThinkPad:~$ hcidump
HCI sniffer - Bluetooth packet analyzer ver 2.2
device: hci0 snap_len: 1028 filter: 0xffffffffffffffff
> HCI Event: Connect Request (0x04) plen 10
    bdaddr F0:65:DD:80:4C:FA class 0x000580 type ACL
> HCI Event: Command Status (0x0f) plen 4
    Accept Connection Request (0x01|0x0009) status 0x00 ncmd 1
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 11 bdaddr F0:65:DD:80:4C:FA type ACL encrypt 0x00
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 11
    Features: 0xbf 0x06 0x86 0x78 0x18 0x1e 0x59 0x87
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Extended Features (0x01|0x001c) status 0x00 ncmd 1
> HCI Event: Read Remote Extended Features (0x23) plen 13
    status 0x00 handle 11 page 1 max 1
    Features: 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> HCI Event: Command Complete (0x0e) plen 10
    Link Key Request Reply (0x01|0x000b) ncmd 1
    status 0x00 bdaddr F0:65:DD:80:4C:FA
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x13 bdaddr F0:65:DD:80:4C:FA name 'ThinkPad Bluetooth Laser Mou'
    Error: Remote User Terminated Connection
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 11 reason 0x13
    Reason: Remote User Terminated Connection
> HCI Event: Connect Request (0x04) plen 10
    bdaddr F0:65:DD:80:4C:FA class 0x000580 type ACL
> HCI Event: Command Status (0x0f) plen 4
    Accept Connection Request (0x01|0x0009) status 0x00 ncmd 1
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 12 bdaddr F0:65:DD:80:4C:FA type ACL encrypt 0x00
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 12
    Features: 0xbf 0x06 0x86 0x78 0x18 0x1e 0x59 0x87
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Extended Features (0x01|0x001c) status 0x00 ncmd 1
> HCI Event: Read Remote Extended Features (0x23) plen 13
    status 0x00 handle 12 page 1 max 1
    Features: 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> HCI Event: Command Complete (0x0e) plen 10
    Link Key Request Reply (0x01|0x000b) ncmd 1
    status 0x00 bdaddr F0:65:DD:80:4C:FA
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x13 bdaddr F0:65:DD:80:4C:FA name 'ThinkPad Bluet'
    Error: Remote User Terminated Connection
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 12 reason 0x13
    Reason: Remote User Terminated Connection
^C
georg@ThinkPad:~$ 

```
same with my smartphone, trying to send a file from it to laptop:
```
georg@ThinkPad:~$ hcidump
HCI sniffer - Bluetooth packet analyzer ver 2.2
device: hci0 snap_len: 1028 filter: 0xffffffffffffffff
> HCI Event: Connect Request (0x04) plen 10
    bdaddr BC:72:B1:61:82:F3 class 0x5a020c type ACL
> HCI Event: Command Status (0x0f) plen 4
    Accept Connection Request (0x01|0x0009) status 0x00 ncmd 1
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 11 bdaddr BC:72:B1:61:82:F3 type ACL encrypt 0x00
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 11
    Features: 0xbf 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Extended Features (0x01|0x001c) status 0x00 ncmd 1
> HCI Event: Read Remote Extended Features (0x23) plen 13
    status 0x00 handle 11 page 1 max 1
    Features: 0x07 0x00 0x00 0x00 0x00 0x00 0x00 0x00
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr BC:72:B1:61:82:F3 name 'GT-N7100'
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 11 reason 0x13
    Reason: Remote User Terminated Connection

```
what happened to BT? is this an official and documented bug in Ubuntu? Can I rollback any updates which caused this?
Thanks.

---

### Post by xc3RnbFO8P on 2014-06-19
Try this (you have to restart):

> sudo apt-get install --reinstall linux-image-$(uname -r)

---

