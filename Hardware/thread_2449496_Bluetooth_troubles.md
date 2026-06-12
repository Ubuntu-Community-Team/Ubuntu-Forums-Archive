---
title: "Bluetooth troubles"
date: 2020-08-27
forum: Hardware
---

### Post by scallions on 2020-08-27
What's up, guys. I've recently purchased a USB bluetooth adapter and some peripherals. Under Windows 10, I am able to easily pair and connect these devices. Under Xubuntu, though, that's a different story. I can see the devices, pair them with the computer, and even connect them. However, within a few seconds, the status bars in the bluetooth manager fade away and the connection is lost. 

Here's what Bluetooth related logs I get from dmesg.

```
[   26.989177] Bluetooth: HCI device and connection manager initialized
[   26.989181] Bluetooth: HCI socket layer initialized
[   26.989183] Bluetooth: L2CAP socket layer initialized
[   26.989189] Bluetooth: SCO socket layer initialized
[   27.182139] rtl8188ee 0000:03:00.0 wlp3s0: renamed from wlan0
[   27.238044] uvcvideo: Found UVC 1.00 device HP TrueVision HD Camera (1bcf:2c9b)
[   27.246887] uvcvideo 2-1:1.0: Entity type for entity Extension 4 was not initialized!
[   27.246891] uvcvideo 2-1:1.0: Entity type for entity Extension 3 was not initialized!
[   27.246892] uvcvideo 2-1:1.0: Entity type for entity Processing 2 was not initialized!
[   27.246893] uvcvideo 2-1:1.0: Entity type for entity Camera 1 was not initialized!
[   27.246976] input: HP TrueVision HD Camera: HP Tru as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input14
[   27.247065] usbcore: registered new interface driver uvcvideo
[   27.247066] USB Video Class driver (1.1.1)
[   27.446467] usbcore: registered new interface driver btusb
[   27.562632] Bluetooth: hci0: BCM: chip id 73
[   27.565699] Bluetooth: hci0: BCM: features 0x07
[   27.583537] Bluetooth: hci0: BCM20702B
[   27.586549] Bluetooth: hci0: BCM20702B0 (002.001.014) build 0000
[   27.600064] bluetooth hci0: Direct firmware load for brcm/BCM20702B0-19ff-0239.hcd failed with error -2
[   27.600072] Bluetooth: hci0: BCM: Patch brcm/BCM20702B0-19ff-0239.hcd not found
[   29.667603] Adding 4077564k swap on /dev/sda7.  Priority:-2 extents:1 across:4077564k FS
[   30.858672] audit: type=1400 audit(1600390687.073:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1103 comm="apparmor_parser"
[   30.858678] audit: type=1400 audit(1600390687.073:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1103 comm="apparmor_parser"
[   30.858681] audit: type=1400 audit(1600390687.073:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=1103 comm="apparmor_parser"
[   30.858684] audit: type=1400 audit(1600390687.073:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1103 comm="apparmor_parser"
[   30.899321] audit: type=1400 audit(1600390687.113:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/core/4917/usr/lib/snapd/snap-confine" pid=1104 comm="apparmor_parser"
[   30.899327] audit: type=1400 audit(1600390687.113:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/core/4917/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=1104 comm="apparmor_parser"
[   30.910926] audit: type=1400 audit(1600390687.125:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1102 comm="apparmor_parser"
[   30.910933] audit: type=1400 audit(1600390687.125:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=1102 comm="apparmor_parser"
[   30.948193] audit: type=1400 audit(1600390687.165:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=1105 comm="apparmor_parser"
[   30.948199] audit: type=1400 audit(1600390687.165:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince//sanitized_helper" pid=1105 comm="apparmor_parser"
[   33.500327] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.500329] Bluetooth: BNEP filters: protocol multicast
[   33.500335] Bluetooth: BNEP socket layer initialized
[   41.481633] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   41.921615] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   41.925421] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   42.026848] r8169 0000:02:00.0 enp2s0: link down
[   42.026956] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   43.337795] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   44.835425] kauditd_printk_skb: 90 callbacks suppressed
[   44.835427] audit: type=1400 audit(1600390701.049:102): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1535 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   44.863492] audit: type=1400 audit(1600390701.077:103): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=1537 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   45.056209] audit: type=1400 audit(1600390701.269:104): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1649 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   45.103044] audit: type=1400 audit(1600390701.317:105): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1537 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   45.330522] audit: type=1400 audit(1600390701.545:106): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1671 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   45.335841] audit: type=1400 audit(1600390701.549:107): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=1670 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   45.336459] audit: type=1400 audit(1600390701.553:108): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1670 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   45.565209] audit: type=1400 audit(1600390701.781:109): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=1711 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   45.565905] audit: type=1400 audit(1600390701.781:110): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1712 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   45.567776] audit: type=1400 audit(1600390701.781:111): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1711 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   69.440214] wlp3s0: authenticate with 74:da:88:18:d8:60
[   69.450427] wlp3s0: send auth to 74:da:88:18:d8:60 (try 1/3)
[   69.453865] wlp3s0: authenticated
[   69.456988] wlp3s0: associate with 74:da:88:18:d8:60 (try 1/3)
[   69.473376] wlp3s0: RX AssocResp from 74:da:88:18:d8:60 (capab=0x411 status=0 aid=7)
[   69.473679] wlp3s0: associated
[   69.777330] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   77.308065] Bluetooth: RFCOMM TTY layer initialized
[   77.308075] Bluetooth: RFCOMM socket layer initialized
[   77.308083] Bluetooth: RFCOMM ver 1.11
[  210.875719] wlp3s0: deauthenticated from 74:da:88:18:d8:60 (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[  210.903338] wlp3s0: authenticate with 74:da:88:18:d8:60
[  210.913610] wlp3s0: send auth to 74:da:88:18:d8:60 (try 1/3)
[  211.015710] wlp3s0: send auth to 74:da:88:18:d8:60 (try 2/3)
[  211.119515] wlp3s0: send auth to 74:da:88:18:d8:60 (try 3/3)
[  211.120671] wlp3s0: authenticated
[  211.123633] wlp3s0: associate with 74:da:88:18:d8:60 (try 1/3)
[  211.227588] wlp3s0: associate with 74:da:88:18:d8:60 (try 2/3)
[  211.331506] wlp3s0: associate with 74:da:88:18:d8:60 (try 3/3)
[  211.435530] wlp3s0: association with 74:da:88:18:d8:60 timed out
[  224.802542] wlp3s0: authenticate with 74:da:88:18:d8:60
[  224.826987] wlp3s0: send auth to 74:da:88:18:d8:60 (try 1/3)
[  224.830879] wlp3s0: authenticated
[  224.833066] wlp3s0: associate with 74:da:88:18:d8:60 (try 1/3)
[  224.854322] wlp3s0: RX AssocResp from 74:da:88:18:d8:60 (capab=0x411 status=0 aid=7)
[  224.854623] wlp3s0: associated

```

---

### Post by scallions on 2020-09-07
bump

---

### Post by scallions on 2020-09-16
Bump

---

### Post by deadflowr on 2020-09-17
Probably start with the seeing the output for 
```
lsusb
```
just to get an idea of what the dongle is.
Please post the results.

---

### Post by scallions on 2020-09-17
> **deadflowr said:**
> Probably start with the seeing the output for 
```
lsusb
```
just to get an idea of what the dongle is.
Please post the results.

Thanks a lot for responding, man. Here's what I get from lsusb:

> Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 19ff:0239 Dynex 
Bus 002 Device 002: ID 1bcf:2c9b Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



Also check out the op, I've added messages from dmesg.

---

### Post by scallions on 2020-09-25
bump

---

### Post by scallions on 2020-09-30
bump

---

### Post by hk42 on 2020-10-02
Are you using any USB3 devices ?
They are known to create interferences in the 2.4GHz band.

---

### Post by scallions on 2020-10-02
Thank you for the reply!

I only have one other device plugged in, and it's just a Logitech wireless mouse. I've confirmed it is not USB 3.0.

---

