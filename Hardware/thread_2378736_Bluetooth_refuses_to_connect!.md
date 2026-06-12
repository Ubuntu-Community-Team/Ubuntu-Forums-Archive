---
title: "Bluetooth refuses to connect!"
date: 2017-11-26
forum: Hardware
---

### Post by winthrop70 on 2017-11-26
[COLOR=#333333][FONT=Ubuntu]I initially asked in General Help, but due to the lack of replies there, I'm narrowing the scope a bit.

So I'm trying to get Bluetooth working on a laptop running Ubuntu 16.04, but it just flat out refuses to connect. I can occasionally get it to pair (it keeps saying "invalid pin"), but it refuses to go any further.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Can someone please help me fix this before I pull all my hair out in frustration?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Thanks in advance![/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Here's logs, and I'll provide any other info upon request.

[/FONT][/COLOR]
/var/log/syslog:


```
Nov 25 19:54:24 timothy kernel: [10004.684066] usb 7-1: new full-speed USB device number 3 using uhci_hcd
Nov 25 19:54:24 timothy kernel: [10004.838186] usb 7-1: device descriptor read/all, error -71
Nov 25 19:54:24 timothy kernel: [10004.964065] usb 7-1: new full-speed USB device number 4 using uhci_hcd
Nov 25 19:54:24 timothy kernel: [10005.126178] usb 7-1: New USB device found, idVendor=0a12, idProduct=0001
Nov 25 19:54:24 timothy kernel: [10005.126185] usb 7-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Nov 25 19:54:24 timothy systemd[1]: Starting Load/Save RF Kill Switch Status...
Nov 25 19:54:24 timothy bluetoothd[923]: Failed to obtain handles for "Service Changed" characteristic
Nov 25 19:54:24 timothy bluetoothd[923]: Not enough free handles to register service
Nov 25 19:54:24 timothy bluetoothd[923]: Error adding Link Loss service
Nov 25 19:54:24 timothy bluetoothd[923]: Not enough free handles to register service
Nov 25 19:54:24 timothy bluetoothd[923]: message repeated 2 times: [ Not enough free handles to register service]
Nov 25 19:54:24 timothy bluetoothd[923]: Current Time Service could not be registered
Nov 25 19:54:24 timothy bluetoothd[923]: gatt-time-server: Input/output error (5)
Nov 25 19:54:24 timothy bluetoothd[923]: Not enough free handles to register service
Nov 25 19:54:24 timothy bluetoothd[923]: Not enough free handles to register service
Nov 25 19:54:24 timothy bluetoothd[923]: Sap driver initialization failed.
Nov 25 19:54:24 timothy bluetoothd[923]: sap-server: Operation not permitted (1)
Nov 25 19:54:24 timothy systemd[1]: Reached target Bluetooth.
Nov 25 19:54:24 timothy systemd[1]: Started Load/Save RF Kill Switch Status.
Nov 25 19:54:25 timothy NetworkManager[921]: <info>  [1511657665.0401] keyfile: add connection in-memory (c751b046-010b-4ba3-a3ee-51bdc57b2b5f,"Studio XL 2 Network")
Nov 25 19:54:25 timothy NetworkManager[921]: <info>  [1511657665.0421] bluez: BT device Studio XL 2 (E4:C8:01:61:0F:1E) added (NAP)
Nov 25 19:54:25 timothy NetworkManager[921]: <info>  [1511657665.0430] manager: (E4:C8:01:61:0F:1E): new Bluetooth device (/org/freedesktop/NetworkManager/Devices/5)
Nov 25 19:54:25 timothy NetworkManager[921]: <info>  [1511657665.0445] device (E4:C8:01:61:0F:1E): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 25 19:54:25 timothy NetworkManager[921]: <info>  [1511657665.0460] keyfile: add connection in-memory (63aa5c15-0d97-4c44-bce4-fbe283ac4b91,"Mrs. Wiggins Network")
Nov 25 19:54:25 timothy NetworkManager[921]: <info>  [1511657665.0478] bluez: BT device Mrs. Wiggins (30:95:E3:96:2E:DB) added (NAP)
Nov 25 19:54:25 timothy NetworkManager[921]: <info>  [1511657665.0487] manager: (30:95:E3:96:2E:DB): new Bluetooth device (/org/freedesktop/NetworkManager/Devices/6)
Nov 25 19:54:25 timothy NetworkManager[921]: <info>  [1511657665.0490] device (30:95:E3:96:2E:DB): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 25 19:54:25 timothy NetworkManager[921]: <info>  [1511657665.0500] device (E4:C8:01:61:0F:1E): state change: unavailable -> disconnected (reason 'none') [20 30 0]
Nov 25 19:54:25 timothy NetworkManager[921]: <info>  [1511657665.0503] device (30:95:E3:96:2E:DB): state change: unavailable -> disconnected (reason 'none') [20 30 0]

```

lsusb:


```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 006 Device 002: ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

journalctl | grep "blue":


```
Nov 25 19:58:51 timothy NetworkManager[802]: <info>  [1511657931.5174] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Nov 25 19:59:05 timothy dbus[786]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service'
Nov 25 19:59:26 timothy bluetoothd[1692]: Bluetooth daemon 5.37
Nov 25 19:59:26 timothy dbus[786]: [system] Successfully activated service 'org.bluez'
Nov 25 19:59:26 timothy bluetoothd[1692]: Starting SDP server
Nov 25 19:59:26 timothy bluetoothd[1692]: Bluetooth management interface 1.14 initialized
Nov 25 19:59:26 timothy bluetoothd[1692]: Failed to obtain handles for "Service Changed" characteristic
Nov 25 19:59:26 timothy bluetoothd[1692]: Not enough free handles to register service
Nov 25 19:59:26 timothy bluetoothd[1692]: Error adding Link Loss service
Nov 25 19:59:26 timothy bluetoothd[1692]: Not enough free handles to register service
Nov 25 19:59:26 timothy bluetoothd[1692]: Not enough free handles to register service
Nov 25 19:59:26 timothy bluetoothd[1692]: Not enough free handles to register service
Nov 25 19:59:26 timothy bluetoothd[1692]: Current Time Service could not be registered
Nov 25 19:59:26 timothy bluetoothd[1692]: gatt-time-server: Input/output error (5)
Nov 25 19:59:26 timothy bluetoothd[1692]: Not enough free handles to register service
Nov 25 19:59:26 timothy bluetoothd[1692]: Not enough free handles to register service
Nov 25 19:59:26 timothy bluetoothd[1692]: Sap driver initialization failed.
Nov 25 19:59:26 timothy bluetoothd[1692]: sap-server: Operation not permitted (1)
Nov 25 19:59:26 timothy NetworkManager[802]: <info>  [1511657966.5925] bluez: use BlueZ version 5
Nov 25 19:59:26 timothy NetworkManager[802]: <info>  [1511657966.7588] bluez: BT device Mrs. Wiggins (30:95:E3:96:2E:DB) added (NAP)
Nov 25 19:59:26 timothy NetworkManager[802]: <info>  [1511657966.7637] bluez: BT device Studio XL 2 (E4:C8:01:61:0F:1E) added (NAP)
Nov 25 19:59:27 timothy dbus[786]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Nov 25 19:59:27 timothy org.blueman.Mechanism[786]: Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Nov 25 19:59:27 timothy org.blueman.Mechanism[786]: Unable to init server: Could not connect: Connection refused
Nov 25 19:59:27 timothy org.blueman.Mechanism[786]: Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Nov 25 19:59:27 timothy org.blueman.Mechanism[786]: Unable to init server: Could not connect: Connection refused
Nov 25 19:59:27 timothy blueman-mechanism[1699]: Starting blueman-mechanism
Nov 25 19:59:27 timothy dbus[786]: [system] Successfully activated service 'org.blueman.Mechanism'
Nov 25 19:59:27 timothy org.blueman.Mechanism[786]: (blueman-mechanism:1699): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Nov 25 19:59:27 timothy blueman-mechanism[1699]: loading Rfcomm
Nov 25 19:59:27 timothy blueman-mechanism[1699]: loading RfKill
Nov 25 19:59:27 timothy blueman-mechanism[1699]: loading Ppp
Nov 25 19:59:27 timothy blueman-mechanism[1699]: loading Network

```

/lib/systemd/system/bluetooth.service:


```
[Unit]
Description=Bluetooth service
Documentation=man:bluetoothd(8)
ConditionPathIsDirectory=/sys/class/bluetooth


[Service]
Type=dbus
BusName=org.bluez
ExecStart=/usr/lib/bluetooth/bluetoothd -C
NotifyAccess=main
#WatchdogSec=10
#Restart=on-failure
CapabilityBoundingSet=CAP_NET_ADMIN CAP_NET_BIND_SERVICE
LimitNPROC=1
ProtectHome=true
ProtectSystem=full


[Install]
WantedBy=bluetooth.target
Alias=dbus-org.bluez.service

```

/lib/systemd/system/rfcomm.service:


```
[Unit]
Description=RFCOMM service
After=bluetooth.service
Requires=bluetooth.service


[Service]
Type=oneshot
ExecStart=/usr/bin/sdptool add SP
ExecStartPost=/bin/hciconfig hci0 piscan
ExecStart=/usr/bin/rfcomm watch hci0 1 getty rfcomm0 115200 vt100


[Install]
WantedBy=multi-user.target

```

---

### Post by howefield on 2017-11-26
Duplicate thread closed.

---

