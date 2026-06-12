---
title: "Belkin F8T012 Bluetooth dongle does not show up after latest system patch"
date: 2011-12-23
forum: Hardware
---

### Post by smartnose on 2011-12-23
I made a fresh installation of UBUNTU 11.10 a month ago. The Belkin F8T012 worked like a charm without any problem. However, after a recent (1 to 2 weeks ago) system update with about 220MB patches. The bluetooth ICON disappeared from my task bar, and UBUNTU wouldn't even recognize the dongle. I ran blue-tooth device manager, and it couldn't find the dongle.

When I do lsusb, it does show a USB device as:


Bus 006 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)


The blue-tooth device manager shows "No bluetooth adapters found"

I tried my dongle on WIndows 7, and it still works. BTW, my laptop had the same problem. After a recent update, it does not recognize my bluetooth dongles anymore.

Can anyone kindly provide some suggestions? Thanks.

---

### Post by smartnose on 2012-01-14
Can anyone help out please?

---

### Post by jefdebruges on 2012-01-20
Had exactly the same problem: I removed all compat-wireless linux modules using Synaptic and after reboot my bluetooth works again.

(look for linux-backports-modules-cw-3.1-*)

---

### Post by ilmkidunya on 2012-01-20
Try to download the latest driver of the Blutooth device and install them if not succeed try google search or driver upgrade process

---

