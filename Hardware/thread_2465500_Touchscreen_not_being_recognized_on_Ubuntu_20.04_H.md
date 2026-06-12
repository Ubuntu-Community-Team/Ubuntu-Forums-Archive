---
title: "Touchscreen not being recognized on Ubuntu 20.04 HP"
date: 2021-08-04
forum: Hardware
---

### Post by gtmoffat23 on 2021-08-04
Trying to get my touchscreen working on Ubuntu 20.04 but not finding much information about it. 
When I run xinput I don't see it mentioned.
[LIST]
[*]Virtual Core XTEST pointer 
[*]Elan Touchoad 
[/LIST]

run  lsusb  it doesnt appear
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0408:51ea Quanta Computer, Inc. HP Wide Vision HD Camera
Bus 001 Device 003: ID 8087:0a2a Intel Corp.  (Bluetooth)
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I tried to follow the Ubuntu guide but when trying to find the serial connection I kept getting permission errors.

screen /dev/ttyS0
[screen is terminating]

Screen
/dev/ttyS1
bash: /dev/ttyS1: Permission denied

Sudo Screen
/dev/ttyS1
bash: /dev/ttyS1: Permission denied

So I cant tell where its connected to and continue trouble shooting

HP Chromebook 15 Krabby Lake
Kernel 5.8.0-63 Generic 

Any help would be appreciated

---

