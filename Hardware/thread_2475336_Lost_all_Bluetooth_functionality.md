---
title: "Lost all Bluetooth functionality"
date: 2022-05-23
forum: Hardware
---

### Post by solitaire on 2022-05-23
Running 22.04 and somehow in the last week I've lost all Bluetooth functionality. motherboard has builtin Bluetooth and I can't turn it on in the settings panel.

Not sure if it's a "code 1di0t" error or not :)

Motherboard : ASUS ROG STRIX B550-I GAMING
uname -a : Linux asus 5.15.0-32-generic #33-Ubuntu SMP Tue May 10 08:40:25 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

I use a Corsair Ironclaw Gaming mouse which uses it's own dongle for connection (2.5 Wireless + Bluetooth) it works in wireless mode and direct usb connection but not in Bluetooth mode.
At the same time I lost the ability to connect my Bluetooth in-ear headphones using the Motherboards inbuilt USB/wifi.

The "Bluetooth Settings" page is saying "No dongles found"

Any ideas of how to check to see what's wrong?
if more info is needed let me know.


lsusb output : 
```

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 1b1c:1b66 Corsair CORSAIR IRONCLAW RGB WIRELESS Gaming Dongle
Bus 003 Device 002: ID 1b1c:1b49 Corsair CORSAIR K70 RGB MK.2 Mechanical Gaming Keyboard
Bus 003 Device 007: ID 1b1c:1b4c Corsair CORSAIR IRONCLAW RGB WIRELESS Gaming Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf2:7750 ENE Technology, Inc. LianLi
Bus 001 Device 002: ID 0b05:1939 ASUSTek Computer, Inc. AURA LED Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

dmesg output:
```

s0l@asus:~ $ sudo dmesg | grep -i bluetooth
[sudo] password for s0l: 
[  122.568855] Bluetooth: Core ver 2.22
[  122.568877] NET: Registered PF_BLUETOOTH protocol family
[  122.568878] Bluetooth: HCI device and connection manager initialized
[  122.568881] Bluetooth: HCI socket layer initialized
[  122.568882] Bluetooth: L2CAP socket layer initialized
[  122.568884] Bluetooth: SCO socket layer initialized
[  122.574972] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  122.574975] Bluetooth: BNEP filters: protocol multicast
[  122.574979] Bluetooth: BNEP socket layer initialized

```

Bluetooth entries in syslog:
```

grep bluetooth /var/log/syslog

May 22 02:56:47 asus bluetoothd[35353]: Terminating
May 22 02:56:47 asus bluetoothd[35353]: Stopping SDP server
May 22 02:56:47 asus bluetoothd[35353]: Exit
May 22 12:09:44 asus NetworkManager[837]: <info>  [1653217784.2213] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-bluetooth.so)
May 23 10:19:24 asus NetworkManager[858]: <info>  [1653297564.2706] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-bluetooth.so)
May 23 10:58:56 asus gnome-control-c[11878]: Failed to register object: An object is already exported for the interface org.bluez.Agent1 at /org/gnome/bluetooth/settings
May 23 11:01:35 asus gnome-control-c[11878]: Failed to register object: An object is already exported for the interface org.bluez.Agent1 at /org/gnome/bluetooth/settings
May 23 11:01:43 asus systemd[2996]: app-gnome-gnome\x2dbluetooth\x2dpanel-11878.scope: Consumed 2.742s CPU time.
May 23 11:02:29 asus NetworkManager[882]: <info>  [1653300149.1739] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-bluetooth.so)
May 23 11:10:51 asus gnome-control-c[11761]: Failed to register object: An object is already exported for the interface org.bluez.Agent1 at /org/gnome/bluetooth/settings
May 23 11:21:03 asus bluetoothd[18188]: Bluetooth daemon 5.64
May 23 11:21:03 asus bluetoothd[18188]: src/main.c:main() Unable to get on D-Bus
May 23 11:21:07 asus bluetoothd[18240]: Bluetooth daemon 5.64
May 23 11:21:07 asus bluetoothd[18240]: Starting SDP server
May 23 11:21:07 asus dbus-daemon[880]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.179' (uid=0 pid=18240 comm="bluetoothd " label="unconfined")
May 23 11:21:07 asus bluetoothd[18240]: Bluetooth management interface 1.21 initialized
May 23 11:23:21 asus bluetoothd[18458]: Bluetooth daemon 5.64
May 23 11:23:21 asus bluetoothd[18458]: D-Bus setup failed: Name already in use
May 23 11:23:21 asus bluetoothd[18458]: src/main.c:main() Unable to get on D-Bus
May 23 11:23:21 asus systemd[1]: bluetooth.service: Main process exited, code=exited, status=1/FAILURE
May 23 11:23:21 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:23:21 asus systemd[1]: bluetooth.service: Scheduled restart job, restart counter is at 1.
May 23 11:23:22 asus bluetoothd[18482]: Bluetooth daemon 5.64
May 23 11:23:22 asus bluetoothd[18482]: D-Bus setup failed: Name already in use
May 23 11:23:22 asus bluetoothd[18482]: src/main.c:main() Unable to get on D-Bus
May 23 11:23:22 asus systemd[1]: bluetooth.service: Main process exited, code=exited, status=1/FAILURE
May 23 11:23:22 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:23:22 asus systemd[1]: bluetooth.service: Scheduled restart job, restart counter is at 2.
May 23 11:23:22 asus bluetoothd[18487]: Bluetooth daemon 5.64
May 23 11:23:22 asus bluetoothd[18487]: D-Bus setup failed: Name already in use
May 23 11:23:22 asus bluetoothd[18487]: src/main.c:main() Unable to get on D-Bus
May 23 11:23:22 asus systemd[1]: bluetooth.service: Main process exited, code=exited, status=1/FAILURE
May 23 11:23:22 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:23:22 asus systemd[1]: bluetooth.service: Scheduled restart job, restart counter is at 3.
May 23 11:23:22 asus bluetoothd[18492]: Bluetooth daemon 5.64
May 23 11:23:22 asus bluetoothd[18492]: D-Bus setup failed: Name already in use
May 23 11:23:22 asus bluetoothd[18492]: src/main.c:main() Unable to get on D-Bus
May 23 11:23:22 asus systemd[1]: bluetooth.service: Main process exited, code=exited, status=1/FAILURE
May 23 11:23:22 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:23:22 asus systemd[1]: bluetooth.service: Scheduled restart job, restart counter is at 4.
May 23 11:23:22 asus bluetoothd[18495]: Bluetooth daemon 5.64
May 23 11:23:22 asus bluetoothd[18495]: D-Bus setup failed: Name already in use
May 23 11:23:22 asus bluetoothd[18495]: src/main.c:main() Unable to get on D-Bus
May 23 11:23:22 asus systemd[1]: bluetooth.service: Main process exited, code=exited, status=1/FAILURE
May 23 11:23:22 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:23:22 asus systemd[1]: bluetooth.service: Scheduled restart job, restart counter is at 5.
May 23 11:23:22 asus systemd[1]: bluetooth.service: Start request repeated too quickly.
May 23 11:23:22 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:24:26 asus bluetoothd[18589]: Bluetooth daemon 5.64
May 23 11:24:26 asus bluetoothd[18589]: D-Bus setup failed: Name already in use
May 23 11:24:26 asus bluetoothd[18589]: src/main.c:main() Unable to get on D-Bus
May 23 11:24:26 asus systemd[1]: bluetooth.service: Main process exited, code=exited, status=1/FAILURE
May 23 11:24:26 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:24:26 asus systemd[1]: bluetooth.service: Scheduled restart job, restart counter is at 1.
May 23 11:24:26 asus bluetoothd[18612]: Bluetooth daemon 5.64
May 23 11:24:26 asus bluetoothd[18612]: D-Bus setup failed: Name already in use
May 23 11:24:26 asus bluetoothd[18612]: src/main.c:main() Unable to get on D-Bus
May 23 11:24:26 asus systemd[1]: bluetooth.service: Main process exited, code=exited, status=1/FAILURE
May 23 11:24:26 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:24:26 asus systemd[1]: bluetooth.service: Scheduled restart job, restart counter is at 2.
May 23 11:24:27 asus bluetoothd[18615]: Bluetooth daemon 5.64
May 23 11:24:27 asus bluetoothd[18615]: D-Bus setup failed: Name already in use
May 23 11:24:27 asus bluetoothd[18615]: src/main.c:main() Unable to get on D-Bus
May 23 11:24:27 asus systemd[1]: bluetooth.service: Main process exited, code=exited, status=1/FAILURE
May 23 11:24:27 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:24:27 asus systemd[1]: bluetooth.service: Scheduled restart job, restart counter is at 3.
May 23 11:24:27 asus bluetoothd[18618]: Bluetooth daemon 5.64
May 23 11:24:27 asus bluetoothd[18618]: D-Bus setup failed: Name already in use
May 23 11:24:27 asus bluetoothd[18618]: src/main.c:main() Unable to get on D-Bus
May 23 11:24:27 asus systemd[1]: bluetooth.service: Main process exited, code=exited, status=1/FAILURE
May 23 11:24:27 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:24:27 asus systemd[1]: bluetooth.service: Scheduled restart job, restart counter is at 4.
May 23 11:24:27 asus bluetoothd[18622]: Bluetooth daemon 5.64
May 23 11:24:27 asus bluetoothd[18622]: D-Bus setup failed: Name already in use
May 23 11:24:27 asus bluetoothd[18622]: src/main.c:main() Unable to get on D-Bus
May 23 11:24:27 asus systemd[1]: bluetooth.service: Main process exited, code=exited, status=1/FAILURE
May 23 11:24:27 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:24:27 asus systemd[1]: bluetooth.service: Scheduled restart job, restart counter is at 5.
May 23 11:24:27 asus systemd[1]: bluetooth.service: Start request repeated too quickly.
May 23 11:24:27 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:24:36 asus systemd[1]: bluetooth.service: Start request repeated too quickly.
May 23 11:24:36 asus systemd[1]: bluetooth.service: Failed with result 'exit-code'.
May 23 11:25:13 asus gnome-control-c[11761]: Failed to register object: An object is already exported for the interface org.bluez.Agent1 at /org/gnome/bluetooth/settings
May 23 11:25:16 asus systemd[2109]: app-gnome-gnome\x2dbluetooth\x2dpanel-11761.scope: Consumed 1.988s CPU time.
May 23 11:25:27 asus bluetoothd[18240]: Terminating
May 23 11:25:27 asus bluetoothd[18240]: Stopping SDP server
May 23 11:25:27 asus bluetoothd[18240]: Exit
May 23 11:26:24 asus NetworkManager[841]: <info>  [1653301584.0431] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-bluetooth.so)
May 23 11:28:21 asus bluetoothd[7098]: Bluetooth daemon 5.64
May 23 11:28:21 asus bluetoothd[7098]: Starting SDP server
May 23 11:28:21 asus dbus-daemon[839]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.109' (uid=0 pid=7098 comm="bluetoothd " label="unconfined")
May 23 11:28:21 asus bluetoothd[7098]: Bluetooth management interface 1.21 initialized
May 23 11:28:34 asus bluetoothd[7098]: Terminating
May 23 11:28:34 asus bluetoothd[7098]: Stopping SDP server
May 23 11:28:34 asus bluetoothd[7098]: Exit
May 23 11:30:35 asus dbus-daemon[3334]: [session uid=1000 pid=3334] Activating via systemd: service name='org.bluez.obex' unit='dbus-org.bluez.obex.service' requested by ':1.153' (uid=1000 pid=10334 comm="gnome-control-center bluetooth " label="unconfined")
May 23 11:38:44 asus bluetoothd[10944]: Bluetooth daemon 5.64
May 23 11:38:44 asus bluetoothd[10944]: Starting SDP server
May 23 11:38:44 asus dbus-daemon[839]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.149' (uid=0 pid=10944 comm="/usr/lib/bluetooth/bluetoothd " label="unconfined")
May 23 11:38:44 asus bluetoothd[10944]: Bluetooth management interface 1.21 initialized

```

lsmod :
```

lsmod | grep blue
Module                  Size  Used by
bluetooth             688128  7 bnep
ecdh_generic           16384  1 bluetooth

```

lspci
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Starship/Matisse IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
00:01.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse GPP Bridge
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:05.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Matisse/Vermeer Data Fabric: Device 18h; Function 7
01:00.0 Non-Volatile memory controller: Phison Electronics Corporation E16 PCIe4 NVMe Controller (rev 01)
02:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43ee
02:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43eb
02:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43e9
03:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43ea
03:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43ea
03:08.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43ea
03:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43ea
05:00.0 Non-Volatile memory controller: Sandisk Corp WD Blue SN500 / PC SN520 NVMe SSD (rev 01)
06:00.0 Network controller: Intel Corporation Wi-Fi 6 AX200 (rev 1a)
07:00.0 Ethernet controller: Intel Corporation Ethernet Controller I225-V (rev 02)
08:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] (rev e1)
08:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]
09:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse PCIe Dummy Function
0a:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Reserved SPP
0a:00.1 Encryption controller: Advanced Micro Devices, Inc. [AMD] Starship/Matisse Cryptographic Coprocessor PSPCPP
0a:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Matisse USB 3.0 Host Controller
0a:00.4 Audio device: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller

```

---

