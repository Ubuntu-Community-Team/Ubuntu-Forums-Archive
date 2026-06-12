---
title: "USB Mouse Delayed Enablement"
date: 2010-11-29
forum: Hardware
---

### Post by ajackm on 2010-11-29
I am using Ubuntu 10.10, upgraded from 10.04.  

On bootup all USB devices take over a minute to be enabled.  So I am unable to loging through GDM for some time.  This wasn't a problem during the betas and only seems to have arrived in the last few weeks.


Under messages in log file viewer
> Nov 29 19:17:22 utgard kernel: [    1.563495] usbcore: registered new interface driver usbfs
Nov 29 19:17:22 utgard kernel: [    1.563503] usbcore: registered new interface driver hub
Nov 29 19:17:22 utgard kernel: [    1.563520] usbcore: registered new device driver usb
Nov 29 19:17:22 utgard kernel: [    2.372286] usb 1-1: new high speed USB device using ehci_hcd and address 2
Nov 29 19:17:22 utgard kernel: [    2.820971] usb 2-4: new high speed USB device using ehci_hcd and address 3
Nov 29 19:17:22 utgard kernel: [   15.666151] rtusb init --->
Nov 29 19:17:22 utgard kernel: [   15.666176] usbcore: registered new interface driver rt2870
Nov 29 19:17:22 utgard kernel: [   33.319676] usb 2-4: new high speed USB device using ehci_hcd and address 4
Nov 29 19:17:22 utgard kernel: [   63.818318] usb 2-4: new high speed USB device using ehci_hcd and address 5
Nov 29 19:17:22 utgard kernel: [   74.330285] usb 2-4: new high speed USB device using ehci_hcd and address 6
Nov 29 19:17:22 utgard kernel: [   85.041716] usb 4-2: new low speed USB device using uhci_hcd and address 2
Nov 29 19:17:22 utgard kernel: [   85.254099] usbcore: registered new interface driver hiddev
Nov 29 19:17:22 utgard kernel: [   85.254212] usbcore: registered new interface driver usbhid
Nov 29 19:17:22 utgard kernel: [   85.254214] usbhid: USB HID core driver
Nov 29 19:17:22 utgard kernel: [   85.270836] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input2
Nov 29 19:17:22 utgard kernel: [   85.270879] microsoft 0003:045E:00F9.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1a.1-2/input0
Nov 29 19:17:22 utgard kernel: [   85.408464] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input3
Nov 29 19:17:22 utgard kernel: [   85.408518] microsoft 0003:045E:00F9.0002: input,hidraw1: USB HID v1.11 Mouse [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1a.1-2/input1
Nov 29 19:17:22 utgard kernel: [   85.511694] usb 6-1: new full speed USB device using uhci_hcd and address 2
Nov 29 19:17:22 utgard kernel: [   85.846076] usbcore: registered new interface driver btusb
Nov 29 19:17:22 utgard kernel: [   86.070200] usb 7-2: new full speed USB device using uhci_hcd and address 2
Nov 29 19:17:38 utgard kernel: [  116.566334] usb 7-2: new full speed USB device using uhci_hcd and address 3
Nov 29 19:18:08 utgard kernel: [  147.062471] usb 7-2: new full speed USB device using uhci_hcd and address 4
Nov 29 19:18:19 utgard kernel: [  157.583296] usb 7-2: new full speed USB device using uhci_hcd and address 5
Nov 29 19:18:29 utgard kernel: [  168.213387] usb 1-1.2: new high speed USB device using ehci_hcd and address 4
Nov 29 19:18:29 utgard kernel: [  168.333737] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x04E8 pid 0x3425
Nov 29 19:18:29 utgard kernel: [  168.333748] usbcore: registered new interface driver usblp
Nov 29 19:18:31 utgard kernel: [  169.638043] usb 1-1.2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1

results of lsusb
> Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:00f9 Microsoft Corp. Wireless Desktop Receiver 3.1
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04e8:3425 Samsung Electronics Co., Ltd 
Bus 001 Device 002: ID 0424:a700 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

dmesg | grep usb
> adam@utgard:~$ dmesg | grep usb
[    1.563495] usbcore: registered new interface driver usbfs
[    1.563503] usbcore: registered new interface driver hub
[    1.563520] usbcore: registered new device driver usb
[    2.372286] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.820971] usb 2-4: new high speed USB device using ehci_hcd and address 3
[   15.666151] rtusb init --->
[   15.666176] usbcore: registered new interface driver rt2870
[   17.900782] usb 2-4: device descriptor read/64, error -110
[   33.090247] usb 2-4: device descriptor read/64, error -110
[   33.319676] usb 2-4: new high speed USB device using ehci_hcd and address 4
[   48.399459] usb 2-4: device descriptor read/64, error -110
[   63.588967] usb 2-4: device descriptor read/64, error -110
[   63.818318] usb 2-4: new high speed USB device using ehci_hcd and address 5
[   74.210599] usb 2-4: device not accepting address 5, error -110
[   74.330285] usb 2-4: new high speed USB device using ehci_hcd and address 6
[   84.722563] usb 2-4: device not accepting address 6, error -110
[   85.041716] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   85.254099] usbcore: registered new interface driver hiddev
[   85.254212] usbcore: registered new interface driver usbhid
[   85.254214] usbhid: USB HID core driver
[   85.270836] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input2
[   85.270879] microsoft 0003:045E:00F9.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1a.1-2/input0
[   85.408464] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input3
[   85.408518] microsoft 0003:045E:00F9.0002: input,hidraw1: USB HID v1.11 Mouse [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1a.1-2/input1
[   85.511694] usb 6-1: new full speed USB device using uhci_hcd and address 2
[   85.846076] usbcore: registered new interface driver btusb
[   86.070200] usb 7-2: new full speed USB device using uhci_hcd and address 2
[  101.149277] usb 7-2: device descriptor read/64, error -110
[  116.336961] usb 7-2: device descriptor read/64, error -110
[  116.566334] usb 7-2: new full speed USB device using uhci_hcd and address 3
[  131.644592] usb 7-2: device descriptor read/64, error -110
[  146.835626] usb 7-2: device descriptor read/64, error -110
[  147.062471] usb 7-2: new full speed USB device using uhci_hcd and address 4
[  157.463632] usb 7-2: device not accepting address 4, error -110
[  157.583296] usb 7-2: new full speed USB device using uhci_hcd and address 5
[  167.974555] usb 7-2: device not accepting address 5, error -110
[  168.213387] usb 1-1.2: new high speed USB device using ehci_hcd and address 4
[  168.333737] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x04E8 pid 0x3425
[  168.333748] usbcore: registered new interface driver usblp
[  169.638043] usb 1-1.2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[ 1388.435571] usb 7-2: new full speed USB device using uhci_hcd and address 6
[ 1403.518266] usb 7-2: device descriptor read/64, error -110
[ 1418.705028] usb 7-2: device descriptor read/64, error -110
[ 1418.934414] usb 7-2: new full speed USB device using uhci_hcd and address 7
[ 1434.023919] usb 7-2: device descriptor read/64, error -110
[ 1449.213156] usb 7-2: device descriptor read/64, error -110
[ 1449.442502] usb 7-2: new full speed USB device using uhci_hcd and address 8
[ 1459.840330] usb 7-2: device not accepting address 8, error -110
[ 1459.964250] usb 7-2: new full speed USB device using uhci_hcd and address 9
[ 1470.345687] usb 7-2: device not accepting address 9, error -110


Kernel version is 2.6.35-23-generic.

Can anyone help?

Adam

---

### Post by gordintoronto on 2010-11-29
What happens when you boot from a LiveCD or flash drive?

---

