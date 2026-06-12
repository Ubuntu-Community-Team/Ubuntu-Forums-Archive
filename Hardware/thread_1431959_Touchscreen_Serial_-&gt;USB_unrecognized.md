---
title: "Touchscreen Serial -&gt;USB unrecognized"
date: 2010-03-17
forum: Hardware
---

### Post by dan1eln1el5en on 2010-03-17
Hey guys, I'm setting up a POS system based on Ubuntu for a friend.
The computer is a nice little AsRock ION 330HT, plenty of USBs but no serial port.
He bought a small 12" Touchscreen, brand is basically "unknown", on it its marked "Precious Line 1212" Ubuntu recognizes it as a TVT FPT1212N and it works fine.

the touchscreen interface is going over a serial port, we bought a serial to USB adapter on eBay.
Doing a lsusb i get the following:
> Bus 001 Device 005: ID 05ac:0221 Apple, Inc. Keyboard (Aluminium) (ISO)
Bus 001 Device 004: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 001 Device 002: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1a86:7523 Unknown HL-340 USB-Serial adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


so Uknown HL-340 USB Serial adapter, my theory is that this is the adapter itself, and we have no connection to the screen.
we also tried plugging it into a Win7 machine, same result, seems like this adapter needs drivers of some sort.

can anyone help me out here ?

---

