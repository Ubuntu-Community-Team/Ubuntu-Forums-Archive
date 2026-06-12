---
title: "Wireless Mouse &amp; Keyboard recognized but not working anymore"
date: 2009-02-25
forum: Hardware
---

### Post by me.tbone on 2009-02-25
Hello anyone,

my wireless desktop (mouse and keyboard) is connected over an usb bluetooth dongle.
The problem is the mouse and keyboard seem not to work anymore (mouse cursor not moving, pressing keys on the keyboard does nothing, since today).
This has happened before weeks ago but plugging the dongle into another slot helped => could have been another problem.

As I am relatively new to Ubuntu, I need help in how to diagnose and hopefully fix the issue.

My System:
- Laptop Lenovo T61p (AMD64)
- Ubuntu 8.10 Intrepid for AMD64 (with latest updates)
- Wireless Desktop: MLK Hama "RF Optical Desktop 3000" 00052443 (=>Chipset is from Sunplus, see output of hciconfig below)

All the things I have tried already (with the help of google and the forum but without success in the sense of fixing my problem):
- stick the dongle into another usb slot
- rebooting with and without the dongle plugged into any slot
- edit /etc/default/bluetooth: changed HID2HCI_ENABLED=1 to HID2HCI_ENABLED=0 and restart the bluetooth service (also reboot)
- try the dongle on another pc (Windows XP System) => there it worked like a charm
- reinstall bluez

Maybe also these outputs could help:

1. dmesg | grep usb:
[ 4080.500197] usb 2-1: USB disconnect, address 9
[ 4083.032113] usb 4-2: new low speed USB device using uhci_hcd and address 10
[ 4083.208539] usb 4-2: configuration #1 chosen from 1 choice
[ 4083.236855] input: MLK HAMA 00052443 as /devices/pci0000:00/0000:00:1d.0/usb4/4-2/4-2:1.0/input/input48
[ 4083.273993] input,hidraw0: USB HID v1.00 Keyboard [MLK HAMA 00052443] on usb-0000:00:1d.0-2
[ 4083.310321] input: MLK HAMA 00052443 as /devices/pci0000:00/0000:00:1d.0/usb4/4-2/4-2:1.1/input/input49
[ 4083.388758] input,hiddev96,hidraw1: USB HID v1.00 Mouse [MLK HAMA 00052443] on usb-0000:00:1d.0-2
=> I only pasted the part appended to the end of output when plugging the dongle out and back in again

2. lsusb:
with the dongle plugged in:
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 17ef:1003 Lenovo 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 010: ID 04fc:05d8 Sunplus Technology Co., Ltd 	<= this is the HAMA dongle
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

3. hciconfig -a:
hci0:	Type: USB
	BD Address: 00:1C:26:D4:E0:A5 ACL MTU: 1017:8 SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:2252 acl:0 sco:0 events:105 errors:0
	TX bytes:1472 acl:0 sco:0 commands:93 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'Neuromancer'
	Class: 0x0a010c
	Service Classes: Networking, Capturing
	Device Class: Computer, Laptop
	HCI Ver: 2.0 (0x3) HCI Rev: 0x212b LMP Ver: 2.0 (0x3) LMP Subver: 0x41d3
	Manufacturer: Broadcom Corporation (15) 
	
If you ask yourself: 
- "Is the reason any updates?". Yes, this could be possible but I have no clue where I could look which updates have been installed since yesterday.
- "Did he play with setting/config files lately?". Yes. I edited /etc/default/bluetooth in the way I described, but edited it back to the original when I had no success.

Any help appreciated.

If someone needs more info or my thread is offtopic or anything else wrong with it, please let me know (this is my first post here + my 6th ever).

Thanks.

---

### Post by me.tbone on 2009-03-10
Can no one point me in the right direction? Or at least tell me why there is no interest to help me with my problem (wrong forum, wrong style, bad english, ...)?

---

### Post by bbear1 on 2009-03-12
Hi,
sorry that I can't provide you the solution but I feel your pain. I too have sought advice from this (and other) forums but have got silence. Sometimes I think the people reading assume we have not done our research (which sometimes, can be the case). Anyway, I have not yet taken the plunge and bought a Bluetooth keyboard but I have done a lot of research and come to the following conclusion:

1. Bluetooth is broken in 8.10 (bug already filed at launchpad, but doesn't seem to be going anywhere), see ..

[https://bugs.launchpad.net/ubuntu-ps3-port/+bug/292042]("https://bugs.launchpad.net/ubuntu-ps3-port/+bug/292042")

2. Some people have got it to work in 8.10 by deleting the Bluetooth stack and changing to some other mode (I can't recall all the details off hand but I can probably point you to a thread discussing it)
3. Some users claim success by ditching the default Bluetooth manager and replacing with the one from the blueman project, see ..

[http://blueman-project.org/]("http://blueman-project.org/")
[http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html]("http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html")

I hope this helps

---

