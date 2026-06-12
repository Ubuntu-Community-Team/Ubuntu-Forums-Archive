---
title: "no hcid.conf in 8.10"
date: 2008-10-31
forum: Hardware
---

### Post by AndyBarker on 2008-10-31
Hi guys.

I'm trying to modify /etc/bluetooth/hcid.conf so i can use 3g mobile broadband from my mobile phone but the file does not exist in that location. All i have is:

audio.conf
input.conf
main.conf
network.conf
rfcomm.conf

I have paired up the notebook with the phone and can browse the memory card etc so bluetooth is working. Does anyone know where this conf file is in 8.10?????

I had this working like a dream in hardy :)

Cheers guys

A.

---

### Post by hyperspaced on 2008-10-31
Same here.

I am using 8.10 on PS3 with a Logitech MediaBoard Pro (bluetooth). Bluetooth was working like a charm in 7.10 (HIDD)

I tried installing bluez-compat (includes hidd) and copied /etc/bluetooth/hcid.conf from my 7.10 installation to 8.10. It doesn't recognize the keyboard automatically. I have to manually connect it (hidd --search   etc...).

---

### Post by bogartuk on 2008-11-06
Having problems with my MediaBoard Pro with a PS3. Tried adding the device using the Bluetooth Applet with no joy. Tried bluez-compat and copying hidd.conf but it is no longer used. 

At the moment I have settled with adding hidd --search to rc.local and pressing the reset button on the keyboard at boot so it is in discover mode. It will do until I have more time to get it sorted!

---

### Post by simon_w on 2008-11-06
I don't know if it will help, but I was having no end of problems with two bluetooth devices until I started using BlueMan, and since then I've had no problems pairing or connecting devices at all.

[BlueMan Website]("http://blueman.tuxfamily.org/")
[PPA Repository]("https://launchpad.net/~blueman/+archive")

Give it a try, perhaps.

Good luck!

---

### Post by bbengtsson on 2008-11-18
I'm a newbie 8.10 and Linux in general.
I'm using a D-Link DBT-120 dongle with a Logitech Bluetooth mouse.
I get this from hciconfig -a:

hci0:	Type: USB
	BD Address: 00:17:9A:2B:06:40 ACL MTU: 384:8 SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN 
	RX bytes:1382 acl:10 sco:0 events:55 errors:0
	TX bytes:603 acl:10 sco:0 commands:36 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'brad-laptop-0'
	Class: 0x0a010c
	Service Classes: Networking, Capturing
	Device Class: Computer, Laptop
	HCI Ver: 2.0 (0x3) HCI Rev: 0x77b LMP Ver: 2.0 (0x3) LMP Subver: 0x77b
	Manufacturer: Cambridge Silicon Radio (10)

So I'm assuming the Dongle is being seen by Ubuntu.
However, when I do an hcitool scan, I don't get any results back.
For some reason the Dongle isn't seeing the mouse or at least not letting Ubuntu know about it.
I tried installing Blueman but was unsuccessful....something about a broken package.

The mouse and dongle work fine when I boot into XP.

The mouse doesn't show up when I right click on the Bluetooth icon at the top of the screen either.

Thanks in advanced for any help
bdb

---

### Post by bbengtsson on 2008-11-18
Update, 
If I press the reset button on the bottom of the Logitech mouse, then run hcitool scan, then I get:
Scanning ...
	00:07:61:3D:A5:00	Bluetooth Travel Mouse
It still seems that I need an hcid.conf file to be able to close the loop.

UPDATE 2:
If I use the BT GUI and use the wizard to set up a new device, no devices are shown until I press the reset button on the Logitech mouse.  Then the BT address for the mouse showed up.  I was then able to pair it and the mouse works fine even after a re_boot.

---

