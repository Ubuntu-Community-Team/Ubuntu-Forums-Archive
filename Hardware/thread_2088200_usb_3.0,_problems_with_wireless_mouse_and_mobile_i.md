---
title: "usb 3.0, problems with wireless mouse and mobile internet dongle"
date: 2012-11-25
forum: Hardware
---

### Post by martinSwe on 2012-11-25
Hi!
I recently bought a new laptop, a Samsung 7 series (700Z5C-S01).
But when I plug in my wireless mouse (Logitec Performance MX, unifying receiver) in a USB 3.0 port, nothing happens. But it works if I plug it into a 2.0 port.
It seems that 3.0 port only works with storage devices because I have the same problem with the mobile internet dongle.

I'm running Ubuntu 12.10 64-bit

And if I run lsusb in the terminal, I get:

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 004: ID 2232:1018  
Bus 002 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 008: ID 0af0:6971 Option Globetrotter HSDPA Modem

```I guess the computer finds the receiver, but it does not work.
So I wonder if there is anyone who has encountered a similar problem and know how to solve it?

BTW the usb 3.0 port works out of the box in window 7

---

