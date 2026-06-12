---
title: "Bluetooth adapter not working"
date: 2018-11-14
forum: Hardware
---

### Post by richdell on 2018-11-14
I installed a Broadcom Corp. BCM20702A0 Bluetooth 4.0 USB adapter in my Xubuntu 18.04 desktop, but can't get it to work. Plugable support talked me through testing including sending me another adapter with no joy. Tried everything I could find on Google with no success.  Lsub shows the device and I can turn it on and off from the panel. bluetoothctl returns :Agent registered, but when I enter "show" I get "No default controller available"start bluetooth. I am hoping someone can help!

---

### Post by jeremy31 on 2018-11-14
What result from terminal for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by richdell on 2018-11-14
rich@rich-desktop:~$ lsusb; dmesg | egrep -i 'blue|firm'
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04a9:190e Canon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 002: ID 05e3:0616 Genesys Logic, Inc. hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 010 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.088942] pci 0000:00:00.0: [Firmware Bug]: reg 0x1c: invalid BAR (can't size)
[    3.965265] Bluetooth: Core ver 2.22
[    3.965280] Bluetooth: HCI device and connection manager initialized
[    3.965282] Bluetooth: HCI socket layer initialized
[    3.965285] Bluetooth: L2CAP socket layer initialized
[    3.965291] Bluetooth: SCO socket layer initialized
[    6.987865] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.987866] Bluetooth: BNEP filters: protocol multicast
[    6.987870] Bluetooth: BNEP socket layer initialized
rich@rich-desktop:~$


In further research, I entered the command: 
 
sudo systemctl start dbus

I got:

Failed to start dbus.service: Operation refused, unit dbus.service may be requested by dependency only (it is configured to refuse manual start/stop).
See system logs and 'systemctl status dbus.service' for details. 

I'm not sure what to do with this.

---

