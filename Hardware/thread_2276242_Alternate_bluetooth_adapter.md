---
title: "Alternate bluetooth adapter?"
date: 2015-05-01
forum: Hardware
---

### Post by b00n on 2015-05-01
I am running a Intel NUC with internal Intel Bluetooth/WiFi adapter.  Bluetooth range is less than I would like so I got an Aircable XR3 [http://www.aircable.net/products/host-xr3.php](http://www.aircable.net/products/host-xr3.php) with tall antenna (donut rather than spherical pattern).  It shows up as

```
$ lsusb | grep -i blue

Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

If I reboot with it plugged in, it comes up as hci0 but either way the built-in is the default adapter -- e.g., if I try to pair headphones, they pair via the built-in adapter.

I tried disabling the internal adapter a couple different ways:

```
$ sudo hciconfig hci1 down
$ sudo hciconfig hciup up
```

This (apparently) lets me pair the headset, but while Settings > Bluetooth > DEVICE shows it as paired, the "Connection" field is always off and cannot be turned on (I tried turning on the headset normally and/or in pairing mode and pairing it.  Nothing either way.)

I also tried disabling it via

```
$ rfkill block 1
```

It seems I can block the builtin but not get the system to use the USB dongle.

When I look in /var/lib/bluetooth, I see both adapters, but while the directory for the builtin has lots of stuff in it, the directly for the dongle is nearly empty -- has "config" but nothing else.

Ubuntu 14.04 64-bit, recently updated and rebooted.

Any hints/tips?  Much 'preciated!

---

### Post by jeremy31 on 2015-05-01
Post the entire ```
lsusb; lspci -nnk | grep -iA2 net
```

---

### Post by b00n on 2015-05-01
> Post the entire

What I did was:

[LIST]
[*]Reboot 
[*]Plug in the Bluetooth USB dongle 
[*]Run the commands 
[/LIST]

```
$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 8087:07da Intel Corp. 
Bus 002 Device 006: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 005: ID 0e8f:0020 GreenAsia Inc. USB to PS/2 Adapter
Bus 002 Device 004: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 002 Device 007: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-V [8086:1559] (rev 04)
    Subsystem: Intel Corporation Device [8086:2054]
    Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
    Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
    Kernel driver in use: iwlwifi
```

---

### Post by jeremy31 on 2015-05-01
Since the Intel bluetooth shouldn't work without firmware, we can make a backup and then delete it from /lib/firmware
```
mkdir intel
```
```
cp /lib/firmware/intel/* ~/intel/
```
```
sudo rm /lib/firmware/intel/*.bseq
```

If that doesn't work, you can use a udev rule similar to [http://projectgus.com/2014/09/blacklisting-a-single-usb-device-from-linux/](http://projectgus.com/2014/09/blacklisting-a-single-usb-device-from-linux/)

```
sudo gedit /etc/udev/rules.d/81-bluetooth-hci.rules
```

and it needs to contain
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="8087", ATTRS{idProduct}=="07da", ATTR{authorized}="0"
```

Save, exit gedit, and reboot

---

### Post by b00n on 2015-05-01
Thanks!  I was concerned about touching everything in [FONT=courier new]/lib/firmware/intel[/FONT], since there's a bunch of things in that directory and (no surprise) a bunch of Intel stuff on a NUC.  Worst-case scenario, I can't boot anymore because something critical stopped working.

So I tried option #2, blacklisting the Intel Bluetooth device as instructed: create the rule file and reboot, it works great.  I see 8087:07da in the lsusb output, but how did you discover that was the Bluetooth device?  (And not, say, 8087:8000.)

I will occasionally plug/unplug the USB dongle -- I will move the machine occasionally and sometimes want to skip the dongle -- but for other folks reading this and using, say, a laptop, it appears you can update udev rules dynamically.  A little bit more info at [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html) for those who want to read more.

---

### Post by jeremy31 on 2015-05-01
> **b00n said:**
> Thanks!  I was concerned about touching everything in [FONT=courier new]/lib/firmware/intel[/FONT], since there's a bunch of things in that directory and (no surprise) a bunch of Intel stuff on a NUC.  Worst-case scenario, I can't boot anymore because something critical stopped working.

So I tried option #2, blacklisting the Intel Bluetooth device as instructed: create the rule file and reboot, it works great.  I see 8087:07da in the lsusb output, but how did you discover that was the Bluetooth device?  (And not, say, 8087:8000.)

I will occasionally plug/unplug the USB dongle -- I will move the machine occasionally and sometimes want to skip the dongle -- but for other folks reading this and using, say, a laptop, it appears you can update udev rules dynamically.  A little bit more info at [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html) for those who want to read more.

/lib/firmware/intel/ only contains bluetooth firmware and there was a chance it wouldn't work because btusb has some generic entries based on what you might find from ```
usb-devices
``` or ```
lsusb -v
```

I found that 8087:07da was the bluetooth using google(first choice as the bluetooth on my Intel 7260 is 8087:07dc IIRC) and I tested the udev rule on my machine with an atheros bluetooth to see if it was still a valid fix

---

### Post by b00n on 2015-05-01
> [FONT=courier new]/lib/firmware/intel/[/FONT] only contains bluetooth firmware

Ah, not at all obvious but definitely safe, thanks.

> what you might find from [FONT=courier new]lsusb -v[/FONT]

I missed the [FONT=courier new]-v[/FONT] option.  In retrospect, I guess it was not obvious to me the internal Bluetooth would even be USB, there's also PCIe in there.  But now that you mention it, [FONT=courier new]lsusb -v[/FONT] shows

```
Bus 002 Device 004: ID 8087:07da Intel Corp. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x07da
  ...
```

Hey, look, it's a Bluetooth adapter!

> I tested the udev rule on my machine with an atheros bluetooth to see if it was still a valid fix         

Thanks again for your help!  And: I hope the next person who needs this can find the thread :-)

---

