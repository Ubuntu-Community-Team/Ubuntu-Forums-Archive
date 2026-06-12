---
title: "Enabling USB mouse on Dell laptop (Hardy)"
date: 2008-07-17
forum: Hardware
---

### Post by stash1071 on 2008-07-17
Hi, I plugged in a couple USB mice to my Dell XPS M1330 laptop running Hardy.  They seem to be detected just fine, but I can't seem to figure out how to "enable" them, the cursor doesn't respond to any movement.

Probably some command, file, or setting I need to work with but I can't seem to find it.  Thanks in advance.

```

$ lsusb
Bus 007 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 006: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

$ dmesg |tail
[  354.169171] usb 3-1: new low speed USB device using uhci_hcd and address 6
[  354.251239] usb 3-1: configuration #1 chosen from 1 choice
[  354.271403] input: Microsoft Microsoft IntelliMouse&#65533; Explorer as /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input12
[  354.320844] input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse&#65533; Explorer] on usb-0000:00:1d.0-1

$ lsusb
...
Bus 003 Device 007: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver

$ dmesg | tail
...
[  445.795485] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input13
[  445.839879] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[  446.109660] usbcore: registered new interface driver lmpcm_usb
[  446.109912] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver

```

---

### Post by stash1071 on 2008-08-14
I guess I should come back and report now my laptop works with any wireless mouse.  I must of been missing something obvious.  Before I could plug it in while it was running to get it work.  Now I can have in before I start my laptop.

---

