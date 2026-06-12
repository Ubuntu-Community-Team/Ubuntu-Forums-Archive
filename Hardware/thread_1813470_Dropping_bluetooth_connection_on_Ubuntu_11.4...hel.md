---
title: "Dropping bluetooth connection on Ubuntu 11.4...help needed."
date: 2011-07-27
forum: Hardware
---

### Post by swift100 on 2011-07-27
hi,

I run Ubuntu 11.4, fresh install, on Acer Travelmate 5520G. I'm having a problem with using a bluetooth headset with it. Whenever I try the connection drops after a while (shorter or longer, this is really erratic...).

When this happens the headset is still listed in the bluetooth preferences but reconnecting is not possible, only through removal and re-discovery.

I've investigated and here are my findings (I'm not a superuser so please treat me as a beginner):

1. The connection with the headset can be established, headset is added to the devices as well as shows in Sound Preferences having been added.

2. Sound can be routed through the headset.

3. The connection drops suddenly without a visible pattern after an arbitrary length of time - 30 sec or can go till disconnected by hand.

4. Re-connection is not possible. The headset disappears from Sound Preferences, although it's still present in bluetooth devices. Attempts to reconnect fail. /var/log/syslog shows:

> Jul 27 22:05:52 alex-TravelMate-5520 bluetoothd[2057]: Function not implemented (38) 

It seems as if after going Bluetooth -> 520Plantronics -> Connect it does connect but just for a sec (checked in terminal). Output from hcitool:

This shows after reconnecting.
> root@alex-TravelMate-5520:~# hcitool con 
Connections: 
	< ACL 00:23:7F:86:59:DB handle 11 state 1 lm MASTER

This showed after reconnecting through GUI.
> root@alex-TravelMate-5520:~# hcitool con 
Connections: 
	< ACL 00:23:7F:86:59:DB handle 11 state 1 lm MASTER **AUTH**

This shows when the headset maintains the connection for a longer while and music is being played through it.
> alex@alex-TravelMate-5520:~$ hcitool con
Connections:
	< SCO 00:23:7F:86:59:DB handle 1 state 1 lm SLAVE 
	< ACL 00:23:7F:86:59:DB handle 12 state 1 lm SLAVE AUTH ENCRYPT


Headset info:
> root@alex-TravelMate-5520:~# hcitool info 00:23:7F:86:59:DB 
Requesting information ... 
	BD Address:  00:23:7F:86:59:DB 
	Device Name: 520Plantronics 
	LMP Version: 2.0 (0x3) LMP Subversion: 0x98a 
	Manufacturer: Cambridge Silicon Radio (10) 
	Features: 0xbc 0xe8 0x01 0x00 0x08 0x08 0x00 0x00 
		<encryption> <slot offset> <timing accuracy> <role switch> 
		<sniff mode> <SCO link> <HV3 packets> <u-law log> <A-law log> 
		<CVSD> <AFH cap. slave> <AFH cap. master>

Laptop bluetooth:
> 
alex@alex-TravelMate-5520:~$ hciconfig 
hci0:	Type: BR/EDR  Bus: USB 
	BD Address: 00:1C:26:E2:F6:2E  ACL MTU: 1017:8  SCO MTU: 64:8 
	UP RUNNING PSCAN 
	RX bytes:5374100 acl:225 sco:105100 events:405 errors:0 
	TX bytes:5364825 acl:189 sco:105078 commands:155 errors:0  

5. To reconnect device needs to be removed, system restarted.

6. Using GUI and terminal (hcitool) give same results.

7. Package **gnome-bluetooth** 2.91.2.is.2.32.0-0ubuntu2 is installed.

8. **Bluez** is installed, ver 4.91-0ubuntu1.

9. Here's what **/var/log/syslog** shows for the connection and the drop a couple of minutes after:

Scenario 1:
> Jul 27 00:23:19 alex-TravelMate-5520 bluetoothd[3484]: Bluetooth deamon 4.91 
Jul 27 00:23:19 alex-TravelMate-5520 bluetoothd[3485]: Starting SDP server 
Jul 27 00:23:19 alex-TravelMate-5520 bluetoothd[3485]: Listening for HCI events on hci0 
Jul 27 00:23:19 alex-TravelMate-5520 NetworkManager[660]: **<warn> bluez error getting default adapter: No such adapter** -> don't know if this has something to do with it...
Jul 27 00:23:19 alex-TravelMate-5520 bluetoothd[3485]: HCI dev 0 up 
Jul 27 00:23:19 alex-TravelMate-5520 bluetoothd[3485]: Adapter /org/bluez/3484/hci0 has been enabled

connected to Bluetooth through terminal, the usual scenario, no more log messages until a couple of minutes later:

Jul 27 00:28:05 alex-TravelMate-5520 bluetoothd[3485]: Function not implemented (38) 
Jul 27 00:29:41 alex-TravelMate-5520 NetworkManager[660]: <info> BT device 00:23:7F:86:59:DB,  removed -> removed manually through gui

Scenario 2:
> Jul 27 21:02:21 alex-TravelMate-5520 kernel: [  997.252035] usb 4-1: new full speed USB device using ohci_hcd and address 2 **&#8594; initiated Bluetooth on laptop**
Jul 27 21:02:21 alex-TravelMate-5520 kernel: [  997.505278] Bluetooth: Core ver 2.15 
Jul 27 21:02:21 alex-TravelMate-5520 kernel: [  997.505315] NET: Registered protocol family 31 
Jul 27 21:02:21 alex-TravelMate-5520 kernel: [  997.505317] Bluetooth: HCI device and connection manager initialized 
Jul 27 21:02:21 alex-TravelMate-5520 kernel: [  997.505321] Bluetooth: HCI socket layer initialized 
Jul 27 21:02:22 alex-TravelMate-5520 kernel: [  997.542237] Bluetooth: Generic Bluetooth USB driver ver 0.6 
Jul 27 21:02:22 alex-TravelMate-5520 kernel: [  997.547558] usbcore: registered new interface driver btusb 
Jul 27 21:02:22 alex-TravelMate-5520 bluetoothd[2056]: Bluetooth deamon 4.91 
Jul 27 21:02:22 alex-TravelMate-5520 bluetoothd[2057]: Starting SDP server 
Jul 27 21:02:22 alex-TravelMate-5520 kernel: [  997.668801] Bluetooth: L2CAP ver 2.15 
Jul 27 21:02:22 alex-TravelMate-5520 kernel: [  997.668807] Bluetooth: L2CAP socket layer initialized 
Jul 27 21:02:22 alex-TravelMate-5520 kernel: [  997.684195] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
Jul 27 21:02:22 alex-TravelMate-5520 kernel: [  997.684200] Bluetooth: BNEP filters: protocol multicast 
Jul 27 21:02:22 alex-TravelMate-5520 kernel: [  997.711735] Bluetooth: SCO (Voice Link) ver 0.6 
Jul 27 21:02:22 alex-TravelMate-5520 kernel: [  997.711740] Bluetooth: SCO socket layer initialized 
Jul 27 21:02:22 alex-TravelMate-5520 bluetoothd[2057]: Listening for HCI events on hci0 
Jul 27 21:02:22 alex-TravelMate-5520 NetworkManager[683]: <warn> bluez error getting default adapter: No such adapter 
Jul 27 21:02:22 alex-TravelMate-5520 bluetoothd[2057]: HCI dev 0 up 
Jul 27 21:02:22 alex-TravelMate-5520 kernel: [  997.776483] Bluetooth: RFCOMM TTY layer initialized 
Jul 27 21:02:22 alex-TravelMate-5520 kernel: [  997.776500] Bluetooth: RFCOMM socket layer initialized 
Jul 27 21:02:22 alex-TravelMate-5520 kernel: [  997.776503] Bluetooth: RFCOMM ver 1.11 
Jul 27 21:02:22 alex-TravelMate-5520 bluetoothd[2057]: Adapter /org/bluez/2056/hci0 has been enabled 
Jul 27 21:03:06 alex-TravelMate-5520 bluetoothd[2057]: Agent replied with an error: org.bluez.Error.Rejected, Pairing request rejected **&#8594; switched headset on, attempt to automatically connect canceled by me**
Jul 27 21:03:18 alex-TravelMate-5520 bluetoothd[2057]: Discovery session 0x20a3f178 with :1.52 activated 
Jul 27 21:03:24 alex-TravelMate-5520 NetworkManager[683]: <info> BT device 00:23:7F:86:59:DB removed 
Jul 27 21:03:33 alex-TravelMate-5520 bluetoothd[2057]: Stopping discovery 
Jul 27 21:03:39 alex-TravelMate-5520 bluetoothd[2057]: last message repeated 2 times 
Jul 27 21:03:39 alex-TravelMate-5520 rtkit-daemon[1211]: Successfully made thread 2074 of process 1396 (n/a) owned by '1000' RT at priority 5. 
Jul 27 21:03:39 alex-TravelMate-5520 rtkit-daemon[1211]: Supervising 4 threads of 1 processes of 1 users. 
Jul 27 21:03:44 alex-TravelMate-5520 bluetoothd[2057]: Audio connection got disconnected 
Jul 27 21:17:01 alex-TravelMate-5520 CRON[2094]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly) 
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165553] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0 **&#8594; started playing music through the headset**
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165570] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0 
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165579] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0 
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165587] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0 
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165595] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0 
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165635] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0 
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165643] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0 
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165651] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0 
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165658] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0 
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165666] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0 
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165674] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0 
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165682] hci_scodata_packet: hci0 SCO packet for unknown connection handle 256 
Jul 27 21:43:29 alex-TravelMate-5520 kernel: [ 3465.165690] hci_scodata_packet: hci0 SCO packet for unknown connection handle 48 **&#8594; such code was repeated for a longer while**

Log after disconnecting manually and trying to reconnect:

> Jul 27 21:55:55 alex-TravelMate-5520 kernel: [ 4211.417499] hci_scodata_packet: hci0 SCO packet for unknown connection handle 65493 &#8594; music being played
Jul 27 21:55:55 alex-TravelMate-5520 kernel: [ 4211.417507] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0 
Jul 27 21:55:55 alex-TravelMate-5520 kernel: [ 4211.427483] hci_scodata_packet: hci0 SCO packet for unknown connection handle 14 
Jul 27 21:55:55 alex-TravelMate-5520 kernel: [ 4211.437487] hci_scodata_packet: hci0 SCO packet for unknown connection handle 2 
Jul 27 21:55:55 alex-TravelMate-5520 kernel: [ 4211.437495] hci_scodata_packet: hci0 SCO packet for unknown connection handle 512 
Jul 27 22:02:39 alex-TravelMate-5520 bluetoothd[2057]: Audio connection got disconnected **&#8594; music stopped**
Jul 27 22:03:09 alex-TravelMate-5520 bluetoothd[2057]: Disconnected from 00:23:7F:86:59:DB, /org/bluez/2056/hci0/dev_00_23_7F_86_59_DB **&#8594; disconnected manually through GUI**
**Jul 27 22:04:30 alex-TravelMate-5520 bluetoothd[2057]: Function not implemented (38)** **&#8594; first attempt to re-connect.**
**Jul 27 22:05:52 alex-TravelMate-5520 bluetoothd[2057]: Function not implemented (38)** **&#8594; second attempt to reconnect**

After restarting the system the headset doesn't connect, removed manually, this time with wifi on added again through discovery. Rather fast disconnect, log shows adapter down.

> Jul 27 22:39:35 alex-TravelMate-5520 kernel: [  839.896315] hci_scodata_packet: hci0 SCO packet for unknown connection handle 89 
Jul 27 22:39:35 alex-TravelMate-5520 kernel: [  839.896319] hci_scodata_packet: hci0 SCO packet for unknown connection handle 52 
Jul 27 22:39:35 alex-TravelMate-5520 kernel: [  839.896322] hci_scodata_packet: hci0 SCO packet for unknown connection handle 88 
Jul 27 22:39:35 alex-TravelMate-5520 kernel: [  839.906308] hci_scodata_packet: hci0 SCO packet for unknown connection handle 47 
Jul 27 22:39:35 alex-TravelMate-5520 kernel: [  839.906316] hci_scodata_packet: hci0 SCO packet for unknown connection handle 83 **&#8594; played music until here, shortly this time**
Jul 27 22:40:25 alex-TravelMate-5520 bluetoothd[1635]: Audio connection got disconnected 
Jul 27 22:40:43 alex-TravelMate-5520 bluetoothd[1635]: Software caused connection abort (103) 
Jul 27 22:40:43 alex-TravelMate-5520 bluetoothd[1635]: headset_resume_complete: resume failed 
Jul 27 22:40:43 alex-TravelMate-5520 pulseaudio[1369]: module-bluetooth-device.c: Received error condition: Input/output error 
Jul 27 22:40:43 alex-TravelMate-5520 bluetoothd[1635]: HCI dev 0 down 
Jul 27 22:40:43 alex-TravelMate-5520 bluetoothd[1635]: Adapter /org/bluez/1632/hci0 has been disabled 
Jul 27 22:40:43 alex-TravelMate-5520 kernel: [  907.932384] usb 4-1: USB disconnect, address 2 
Jul 27 22:40:43 alex-TravelMate-5520 kernel: [  907.932894] btusb_bulk_complete: hci0 urb f0b03000 failed to resubmit (19) 
Jul 27 22:40:43 alex-TravelMate-5520 kernel: [  907.932911] btusb_intr_complete: hci0 urb f0b03380 failed to resubmit (19) 
Jul 27 22:40:43 alex-TravelMate-5520 kernel: [  907.933893] btusb_bulk_complete: hci0 urb f0b03180 failed to resubmit (19) 
Jul 27 22:40:43 alex-TravelMate-5520 kernel: [  907.934076] btusb_send_frame: hci0 urb f6edeb80 submission failed 
Jul 27 22:40:43 alex-TravelMate-5520 kernel: [  907.941928] __set_isoc_interface: hci0 setting interface failed (19) 
Jul 27 22:40:43 alex-TravelMate-5520 bluetoothd[1635]: HCI dev 0 unregistered 
Jul 27 22:40:43 alex-TravelMate-5520 bluetoothd[1635]: Stopping hci0 event socket 
Jul 27 22:40:43 alex-TravelMate-5520 bluetoothd[1635]: Unregister path: /org/bluez/1632/hci0 
Jul 27 22:40:44 alex-TravelMate-5520 kernel: [  908.816069] usb 4-1: new full speed USB device using ohci_hcd and address 3 
Jul 27 22:40:44 alex-TravelMate-5520 bluetoothd[1635]: HCI dev 0 registered 
Jul 27 22:40:44 alex-TravelMate-5520 bluetoothd[1635]: Listening for HCI events on hci0 
Jul 27 22:40:44 alex-TravelMate-5520 bluetoothd[1635]: HCI dev 0 up 
Jul 27 22:40:44 alex-TravelMate-5520 bluetoothd[1635]: Adapter /org/bluez/1632/hci0 has been enabled

Removed device manually, restarted, made connection again through discovery. Wifi on. Connection was sustained for longer.

Could someone advise me what to do here? I'm not familiar with how bluetooth is setup in the system. It seems that something causes bluetooth to drop the connection, may knock down the device and when reconnecting bluetooth daemon will give **bluetoothd[2057]: Function not implemented (38)**.

Ant ideas how to make it work normally??

Thanks in advance!

---

### Post by swift100 on 2011-07-29
No ideas? Anyone?

Now the bluetooth icon disappeared from the notification area and when i run the bluetooth applet i get - "Your computer does not have any Bluetooth adapters plugged in"...

---

