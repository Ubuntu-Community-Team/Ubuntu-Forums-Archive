---
title: "Ubuntu 14.10 Lenovo Yoga 3 Pro Issues"
date: 2014-12-19
forum: Hardware
---

### Post by sgarib on 2014-12-19
I have installed Ubuntu 14.10 in my new toy, which I love: Lenovo Yoga 3 Pro.

I have some issues that I have not been able to work around, and I would like to report them, to see if anyone has suffered the same, and have some tips to share, or just confirm same behavior.

0.- Wifi is working after blacklisting idea_laptop as written in a lot of posts. So, no issue there.

1.- Graphics: Graphics works out of the box at native resolution. I change the scale in Unity and Firefox and it actually  works fine, but with some minor annoyances (ie: mousse pointer is very small in some objects, as the panel). I ended up, though, working at 1920x1080, wish is equivalent at my eyes.

**The problem appears when I connect a second monitor.** Unity starts to behave randomly wrong. Some fonts and UI controls disappear, some windows are not rendered correctly, and some times the desktop background image is turned black. I don't know if this is a 14.10 problem, or a driver problem. I neither have knowledge nor know tools to figure it out.

2.- Bluetooth: 

Bluetooth looks that it works. But it does not. Basically, a see the bluetooth device, can query it, but can't find nor connect to devices. 

If I do: ```
hciconfig
```
I get :

```

 hci0:	Type: BR/EDR  Bus: USB
	BD Address: 38:B1:DB:E2:D4:B0  ACL MTU: 1021:8  SCO MTU: 64:1
	UP RUNNING PSCAN ISCAN 
	RX bytes:636 acl:0 sco:0 events:41 errors:0
	TX bytes:1442 acl:0 sco:0 commands:41 errors:0

```

But scan does not report devices, and from other devices I can't see my laptop, 

In some occasion, and this is the crazy part. I have seen my phone. But could not connect.

I hope someone could help or share information. Thanks in advance!.

PD:

Some more info:

```

bluez-test-adapter list
 [ /org/bluez/536/hci0 ]
    Class = 0x000000
    Devices = dbus.Array([], signature=dbus.Signature('o'), variant_level=1)
    Pairable = 1
    Powered = 1
    DiscoverableTimeout = 0
    Discoverable = 1
    UUIDs = dbus.Array([dbus.String('00001000-0000-1000-8000-00805f9b34fb'), dbus.String('00001001-0000-1000-8000-00805f9b34fb'), dbus.String('0000112d-0000-1000-8000-00805f9b34fb'), dbus.String('00001112-0000-1000-8000-00805f9b34fb'), dbus.String('0000111f-0000-1000-8000-00805f9b34fb'), dbus.String('0000111e-0000-1000-8000-00805f9b34fb'), dbus.String('0000110c-0000-1000-8000-00805f9b34fb'), dbus.String('0000110e-0000-1000-8000-00805f9b34fb'), dbus.String('0000110a-0000-1000-8000-00805f9b34fb'), dbus.String('0000110b-0000-1000-8000-00805f9b34fb')], signature=dbus.Signature('s'), variant_level=1)
    PairableTimeout = 0
    Address = 38:B1:DB:E2:D4:B0
    Discovering = 0
    Name = ubuntu-0

```

---

### Post by Pilot6 on 2014-12-19
The problem may be in blacklisting ideapad_laptop.
That problem is already fixed in kernel 3.16.0-29.29, which is in proposed repository right now.
So no more blacklisting is needed.

Please, give output of

lsusb
rfkill list

---

### Post by sgarib on 2014-12-19
I'll try removing it, meanwhile:

lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 005: ID 5986:0535 Acer, Inc 
Bus 001 Device 004: ID 0489:e07a Foxconn / Hon Hai 
Bus 001 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by sgarib on 2014-12-19
Also:

lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 08)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 08)
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Camarillo Device (rev 08)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
01:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)

---

### Post by Pilot6 on 2014-12-19
You have a broadcom [COLOR=#000000]0489:e07a module.
Try to find a solution in the web. There must be some drivers.[/COLOR]

---

### Post by Pilot6 on 2014-12-19
This is one of them.
[http://dhanar10.blogspot.com.br/2014/05/bcm43142-bluetooth-getting-it-to-work.html](http://dhanar10.blogspot.com.br/2014/05/bcm43142-bluetooth-getting-it-to-work.html)

---

### Post by joskov777 on 2015-01-14
[FONT=arial narrow][I]1.- Graphics: Graphics works out of the box at native resolution. I change the scale in Unity and Firefox and it actually  works fine, but with some minor annoyances (ie: mousse pointer is very small in some objects, as the panel). I ended up, though, working at 1920x1080, wish is equivalent at my eyes.

**The problem appears when I connect a second monitor.** Unity starts to behave randomly wrong. Some fonts and UI controls disappear, some windows are not rendered correctly, and some times the desktop background image is turned black. I don't know if this is a 14.10 problem, or a driver problem. I neither have knowledge nor know tools to figure it ou[/I]t.[/FONT]


I have exactly the same problem. My temporary solution for "serious work" is to use only external monitor connected to microUSB and switch off the build-in display (System settings - Display). Any solution available to use dual display?

---

