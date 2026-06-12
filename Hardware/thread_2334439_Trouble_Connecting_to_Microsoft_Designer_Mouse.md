---
title: "Trouble Connecting to Microsoft Designer Mouse"
date: 2016-08-19
forum: Hardware
---

### Post by themeadows94 on 2016-08-19
Using Ubuntu Gnome 16.04 on an Intel NUC . Dual booting with Win 10, where the mouse works fine. 

Blueman wasn't working so I researched a little and got instructions for bluetoothctl. The results:

```
matthew@matthew-desktop:~$ bluetoothctl[NEW] Controller 00:C2:C6:CB:E5:CA matthew-desktop [default]
[NEW] Device 6C:71:D9:2F:61:62 Bluetooth USB Host Controller
[NEW] Device B8:09:8A:BB:95:B6 thabo’s iMac
[NEW] Device 00:26:08:CA:99:B6 Jule
[NEW] Device 64:27:37:83:35:CD TOM-PC
[NEW] Device 7C:2F:80:78:93:47 SL910
[NEW] Device 88:C6:26:9C:F6:D4 UE BOOM 2
[NEW] Device CA:FA:3A:7B:F8:8D Designer Mouse
[CHG] Device CA:FA:3A:7B:F8:8D UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Device CA:FA:3A:7B:F8:8D UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Device CA:FA:3A:7B:F8:8D UUIDs: 0000180a-0000-1000-8000-00805f9b34fb
[CHG] Device CA:FA:3A:7B:F8:8D UUIDs: 0000180f-0000-1000-8000-00805f9b34fb
[CHG] Device CA:FA:3A:7B:F8:8D UUIDs: 00001812-0000-1000-8000-00805f9b34fb
[CHG] Device CA:FA:3A:7B:F8:8D Appearance: 0x03c2
[CHG] Device CA:FA:3A:7B:F8:8D Icon: input-mouse
[bluetooth]# trust CA:FA:3A:7B:F8:8D
[CHG] Device CA:FA:3A:7B:F8:8D Trusted: yes
Changing CA:FA:3A:7B:F8:8D trust succeeded
[bluetooth]# pair CA:FA:3A:7B:F8:8D
Attempting to pair with CA:FA:3A:7B:F8:8D
[CHG] Device CA:FA:3A:7B:F8:8D Paired: yes
Pairing successful
[bluetooth]# connect CA:FA:3A:7B:F8:8D
Attempting to connect to CA:FA:3A:7B:F8:8D
Connection successful
[CHG] Device 6C:71:D9:2F:61:62 RSSI: -89
[CHG] Device 6C:71:D9:2F:61:62 RSSI: -81
[CHG] Device 00:26:08:CA:99:B6 RSSI: -90
[CHG] Device 00:26:08:CA:99:B6 RSSI: -78
[CHG] Device CA:FA:3A:7B:F8:8D Connected: no
[bluetooth]# connect CA:FA:3A:7B:F8:8D
Attempting to connect to CA:FA:3A:7B:F8:8D
[CHG] Device 00:26:08:CA:99:B6 RSSI: -86
[CHG] Device CA:FA:3A:7B:F8:8D Connected: yes
Connection successful
[CHG] Device 7C:2F:80:78:93:47 RSSI: -83
[CHG] Device 00:26:08:CA:99:B6 RSSI: -78
[CHG] Device 00:26:08:CA:99:B6 RSSI: -88



```

So the mouse appears to be connected, but the cursor is not responsive. (It is responsive to the Logitech T650 touchpad I'm also using).

Anyone have any ideas on how to debug/rectify this? Thanks!

---

