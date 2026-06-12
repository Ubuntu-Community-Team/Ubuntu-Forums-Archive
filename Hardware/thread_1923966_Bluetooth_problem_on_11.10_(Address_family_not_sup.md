---
title: "Bluetooth problem on 11.10 (Address family not supported)"
date: 2012-02-11
forum: Hardware
---

### Post by Aikidoka69 on 2012-02-11
I've added a BT dongle after my initial install.  It appears that my bluetooth daemon cannot start though.  I've tried looking up a few of the errors but have come up short so far.  Perhaps I have a package missing?

from syslog
Feb 11 16:40:45 aikibuntu bluetoothd[2028]: Bluetooth daemon 4.96
Feb 11 16:40:45 aikibuntu bluetoothd[2028]: Starting SDP server
Feb 11 16:40:45 aikibuntu bluetoothd[2028]: opening L2CAP socket: Address family not supported by protocol
Feb 11 16:40:45 aikibuntu bluetoothd[2028]: Server initialization failed
Feb 11 16:40:46 aikibuntu bluetoothd[2028]: Failed to open control socket: Address family not supported by protocol (97)
Feb 11 16:40:46 aikibuntu bluetoothd[2028]: Can't init bnep module
Feb 11 16:40:46 aikibuntu bluetoothd[2028]: Failed to init network plugin
Feb 11 16:40:46 aikibuntu bluetoothd[2028]: Unable to start SCO server socket
Feb 11 16:40:46 aikibuntu bluetoothd[2028]: Failed to init audio plugin
Feb 11 16:40:46 aikibuntu bluetoothd[2028]: Can't open HCI socket: Address family not supported by protocol (97)
Feb 11 16:40:46 aikibuntu bluetoothd[2028]: adapter_ops_setup failed
Feb 11 16:40:46 aikibuntu pulseaudio[1615]: [pulseaudio] bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.NoReply
Feb 11 16:40:46 aikibuntu NetworkManager[773]: <warn> bluez error getting default adapter: Message did not receive a reply (timeout by message bus)

I am running the linux-virtual kernel 3.0.0-15.

---

### Post by mciverza on 2012-10-12
> **Aikidoka69 said:**
> I've added a BT dongle after my initial install.  It appears that my bluetooth daemon cannot start though.  I've tried looking up a few of the errors but have come up short \

I get the same problem on a Dell Vostro 3550
running Kernel 3.2.0-30-generic x86_64 GNU/Linux 
on Ubuntu precise

When activating bluetooth, the device appears when 'lsusb' is used.
It is "ID 8086:0189 Intel Corp"

My syslog repeats the following until init kills the service with a "spawning too fast" message.


Oct 12 16:34:41 shrooms bluetoothd[17659]: Bluetooth daemon 4.98
Oct 12 16:34:41 shrooms bluetoothd[17659]: Starting SDP server
Oct 12 16:34:41 shrooms bluetoothd[17659]: opening L2CAP socket: Address family not supported by protocol
Oct 12 16:34:41 shrooms bluetoothd[17659]: Server initialization failed
Oct 12 16:34:41 shrooms bluetoothd[17659]: Failed to init alert plugin
Oct 12 16:34:41 shrooms bluetoothd[17659]: Failed to init time plugin
Oct 12 16:34:41 shrooms bluetoothd[17659]: Failed to init proximity plugin
Oct 12 16:34:41 shrooms bluetoothd[17659]: Failed to open control socket: Address family not supported by protocol (97)
Oct 12 16:34:41 shrooms bluetoothd[17659]: Can't init bnep module
Oct 12 16:34:41 shrooms bluetoothd[17659]: Failed to init network plugin
Oct 12 16:34:41 shrooms bluetoothd[17659]: Unable to start SCO server socket
Oct 12 16:34:41 shrooms bluetoothd[17659]: Failed to init audio plugin
Oct 12 16:34:41 shrooms bluetoothd[17659]: Failed to init gatt_example plugin
Oct 12 16:34:41 shrooms bluetoothd[17659]: Can't open HCI socket: Address family not supported by protocol (97)
Oct 12 16:34:41 shrooms bluetoothd[17659]: adapter_ops_setup failed
Oct 12 16:34:41 shrooms pulseaudio[2870]: [pulseaudio] bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.NoReply
Oct 12 16:34:41 shrooms NetworkManager[1538]: <warn> bluez error getting default adapter: Message did not receive a reply (timeout by message bus)
Oct 12 16:34:41 shrooms kernel: [30511.365118] init: bluetooth main process (17659) terminated with status 1
Oct 12 16:34:41 shrooms kernel: [30511.365194] init: bluetooth respawning too fast, stopped
Oct 12 16:34:41 shrooms bluez: Stopping uarts
Oct 12 16:34:41 shrooms bluez: Stopping rfcomm

---

