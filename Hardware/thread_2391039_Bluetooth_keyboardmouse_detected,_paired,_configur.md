---
title: "Bluetooth keyboard/mouse detected, paired, configured, but doesn't move mouse/keys"
date: 2018-05-05
forum: Hardware
---

### Post by silentstone on 2018-05-05
My small wireless keyboard/mouse touchpad combo device worked fine on Xubuntu 14.04 and 16.04, but problem on Xubuntu 18.04. Bluetooth detects it, pairs, then configures by connecting to HID service.  Everything looks great until I actually try to use the keys or move the mouse; they don't move.  The bluetooth connection stays alive, and keys/mouse on built-in devices and external USB keyboard remain functional.  Yet, the bluetooth device fails to type or move mouse pointer.

How can I get the bluetooth keyboard/mouse functioning on Xubuntu 18.04?  What changed to affect mouse/keyboard devices between different distro versions?

---

### Post by silentstone on 2018-05-05
More hardware details.  Troublesome device is a _Rii Mini i8+_, compact wireless keyboard and mouse touchpad combo.  It uses a bluetooth connection, and has non-removable battery which should be fully charged by now.  My laptop has built-in bluetooth, and is running Xubuntu 18.04.

The bluetooth manager identifies the keyboard as "Bluetooth 3.0 Macro Keyboard", and after pairing, connects it to Human Interface Device service.

**lsusb** output:
Bus 002 Device 004: ID 04ca:3006 Lite-On Technology Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 001 Device 003: ID 1bcf:2c18 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 152d:8561 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**dmesg** output after connecting keyboard:
[ 8813.224025] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[ 8813.224031] Bluetooth: HIDP socket layer initialized
[ 9061.437536] apple 0005:05AC:022C.0002: unknown main item tag 0x0
[ 9061.438231] input: Bluetooth 3.0 Macro Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:21/0005:05AC:022C.0002/input/input14
[ 9061.440733] apple 0005:05AC:022C.0002: input,hidraw1: BLUETOOTH HID v1.1b Keyboard [Bluetooth 3.0 Macro Keyboard] on 2c:d0:5a:0b:48:2f

**dmesg |grep -i blue**:
[   14.052939] Bluetooth: Core ver 2.22
[   14.052958] Bluetooth: HCI device and connection manager initialized
[   14.052961] Bluetooth: HCI socket layer initialized
[   14.052963] Bluetooth: L2CAP socket layer initialized
[   14.052969] Bluetooth: SCO socket layer initialized
[   17.777833] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.777835] Bluetooth: BNEP filters: protocol multicast
[   17.777840] Bluetooth: BNEP socket layer initialized
[  175.519318] Bluetooth: RFCOMM TTY layer initialized
[  175.519323] Bluetooth: RFCOMM socket layer initialized
[  175.519330] Bluetooth: RFCOMM ver 1.11
[ 8813.224025] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[ 8813.224031] Bluetooth: HIDP socket layer initialized
[ 9061.438231] input: Bluetooth 3.0 Macro Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:21/0005:05AC:022C.0002/input/input14
[ 9061.440733] apple 0005:05AC:022C.0002: input,hidraw1: BLUETOOTH HID v1.1b Keyboard [Bluetooth 3.0 Macro Keyboard] on 2c:d0:5a:0b:48:2f

**hcitool scan:**
Scanning ...

and no other output from that command.

---

### Post by silentstone on 2018-05-17
well, it's working now!  apparently, NUMLOCK was on and that interfered with both the mouse and typing functions of the bluetooth keyboard.  i don't understand how, but turning that off instantly allowed the device to control mouse and keys.

---

### Post by ckrzen on 2018-08-07
Hi @silentstone,

It is probably my bug-report to have the numlockx package added to Xubuntu in 18.04 that bit ya. It is a "Good Thing"(R) on desktops with traditional 105 keys+numpad devices as it more closely matches expectations in the user environment for those migrating from Windows, etc..

In case you or anyone else needs a quick-fix for the situation on laptops or Bluetooth devices, etc., just change the NUMLOCK variable to 'off' in the defaults file for numlockx:[INDENT]```
$ editor /etc/default/numlockx 


# Configuration file for numlockx


# State of numlog on start of X session
# Accepts following options:
# auto - turns numlock on unless ran on laptop
# on - turns numlock on
# off - turns numlock off
# keep - does not change numlock state
# toggle - toggles numlock state
NUMLOCK=off
```[/INDENT]

---

