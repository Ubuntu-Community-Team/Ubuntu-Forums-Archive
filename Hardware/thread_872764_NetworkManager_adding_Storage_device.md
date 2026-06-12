---
title: "NetworkManager adding Storage device"
date: 2008-07-28
forum: Hardware
---

### Post by rahmath on 2008-07-28
Dear Techies,

I dont understand what is the role of NetworkManager in adding a storage device; see the following log entry from my debug.log

PC: Dell Optiplex 745
OS: ubuntu hardy

Jul 28 16:33:20 testmachine NetworkManager: <debug> [1217252000.280829] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_TS_H653A'). 



Any ideas???

---

### Post by rahmath on 2008-07-28
This too from the same log;;;

Jul 28 16:33:20 testmachine NetworkManager: <debug> [1217252000.287785] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jul 28 16:33:22 testmachine NetworkManager: <debug> [1217252002.881580] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2992_drm_i915_card0').


about first line, Bluetooth, we can guess that, its related the network. What about the pci (there is no PCI card itself, and Network card is built in)

Anything hits on ur mind???

---

### Post by rahmath on 2008-07-28
Info related to Network card ( forgot to include in the last post; sorry)

On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: Broadcom 5751 NetXtreme Gigabit Controller


Thats it! any idea!!!

---

