---
title: "Realtek RTL8188SU asus USB N10 wireless usb dongle too slow!"
date: 2014-07-27
forum: Hardware
---

### Post by bloff-sites on 2014-07-27
Hello everyone,

I have an ASUS USB-N10 Wireless-N150 USB dongle, I am running Linux Mint 17 KDE (based off kubuntu 14.04 LTS).

The pen is detected, and I can connect to some networks, but:

- I can not connect to WPA protected networks.
-  The speed is somehow limited to roughly 0.6 Mbit/s (that's roughly 75  Kbyte/s). But the speed of my network is much higher (other computers in  the same network get roughly 8Mbit/s).

Here is some information:

```

$ lsusb
...
Bus 003 Device 002: ID 0b05:1786 ASUSTek Computer, Inc. USB-N10 802.11n Network Adapter [Realtek RTL8188SU]
...
```

```

$dmesg
...
[  390.001031] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[  390.001377] r8712u: Staging version
[  390.001384] r8712u: register rtl8712_netdev_ops to netdev_ops
[  390.001386] usb 3-2: r8712u: USB_SPEED_HIGH with 4 endpoints
[  390.001636] usb 3-2: r8712u: Boot from EFUSE: Autoload OK
[  390.320237] usb 3-2: r8712u: CustomerID = 0x0010
[  390.320243] usb 3-2: r8712u: MAC Address from efuse = bc:ee:7b:85:5b:f1
[  390.320246] usb 3-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  390.320847] usbcore: registered new interface driver r8712u
[  391.025133] r8712u 3-2:1.0 wlan0: 1 RCR=0x153f00e
[  391.025716] r8712u 3-2:1.0 wlan0: 2 RCR=0x553f00e
...

```

Not sure if anything else is needed.

Any idea on how I can fix this?

Thank you,
Bruno

---

