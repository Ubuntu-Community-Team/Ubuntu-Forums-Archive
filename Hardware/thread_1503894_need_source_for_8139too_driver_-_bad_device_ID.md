---
title: "need source for 8139too driver - bad device ID"
date: 2010-06-07
forum: Hardware
---

### Post by SeeJayDee on 2010-06-07
Hi all,

The local server I'm in the process of setting up uses a realtek RTL8139C NIC. It is running ubuntu 10.04 with kernel 2.6.32-21-generic-pae.

However, the NIC isn't recognized by either rtl8139, 8139cp or 8139too modules.

```

lspci | grep Ethernet
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. **Device 8331** (rev 10)
```I think this is because its device ID is '8331' not '8139' for some reason (although 'RTL8139C' is printed on the chipset). - so it isn't recognized as an 8139 NIC.
It used to work so... it still should...? we shall see...



I found the source code for the 8139too driver at [http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/drivers/net/8139too.c](http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/drivers/net/8139too.c), but it seems to be in html format.

I want to add driver support for my dodgy NIC by adding the line:```
{0x10ec, 0x8331, PCI_ANY_ID, PCI_ANY_ID, 0, 0, RTL8139 },
``` under DEFINE_PCI_DEVICE_TABLE, and re-compiling the driver.

Then, I'll overwrite the old 8139too.ko ---
```
sudo cp /blah/8139too.ko /lib/modules/2.6.32-21-generic/kernel/drivers/net/8139too.ko
```If anyone could give me any tips on how to do this, or point me to where I can download 8139too.c and related files, I'd be most grateful.


OR if there's a way to force/spoof the driver into claiming the device, that'd be even better.

edit: Just bought new NIC nvm guys

---

