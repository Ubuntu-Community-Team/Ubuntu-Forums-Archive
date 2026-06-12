---
title: "Bluetooth Not Working - 14.04 Beta"
date: 2014-04-11
forum: Hardware
---

### Post by gwinston99 on 2014-04-11
The built in bluetooth adapter on my HP Laptop (HP Compaq 6910p) stopped working with recent kernel upgrade in 13.10, still not working in 14.04 beta:

Output of dmesg | grep bluetooth:

$ dmesg | grep tooth
[   32.530825] Bluetooth: Core ver 2.17
[   32.530851] Bluetooth: HCI device and connection manager initialized
[   32.531046] Bluetooth: HCI socket layer initialized
[   32.531051] Bluetooth: L2CAP socket layer initialized
[   32.531057] Bluetooth: SCO socket layer initialized
[   32.551468] Bluetooth: RFCOMM TTY layer initialized
[   32.551480] Bluetooth: RFCOMM socket layer initialized
[   32.551487] Bluetooth: RFCOMM ver 1.11
[   32.556572] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.556575] Bluetooth: BNEP filters: protocol multicast
[   32.556584] Bluetooth: BNEP socket layer initialized

................................................................................................
Output of hcitool dev:

~$ hcitool dev
Devices:

................................................................................................

Output of rfkill list:

$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

....................................................................................................
I tried installing linux-firmware-nonfree, but this did not help.

Please provide further troubleshooting steps

---

### Post by Ubi_one_2014 on 2014-04-12
what kernel are you using curently?

you can find this by typing uname -r as non-root in the terminal

for me,  i have kernel 3.14 installed on kubuntu 13.10, and the build-in bluetooth on my dell laptop works like it ever did

---

