---
title: "Bluetooth Hardware Version?"
date: 2011-10-10
forum: Hardware
---

### Post by RMOP on 2011-10-10
Ubuntu 11.04 64-bit Gnome Desktop

Is there an easy way to determine my BT HARDWARE version from within Ubuntu? My ThinkPad x120e is supposed to have BT 3.0, but the 3.0 driver update fails to install within W7. I thought I might get a better view of the actual HW from Ubuntu.

Any help here? Thanks.

---

### Post by RMOP on 2011-11-16
hwinfo reports:

52: USB 00.0: 11500 Bluetooth Device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_a5c_217f_CCAF78ED1915_if0
  Unique ID: eqBD.tRab1q52Pl0
  Parent ID: uIhY.7qWCOCfUJwE
  SysFS ID: /devices/pci0000:00/0000:00:12.0/usb3/3-4/3-4:1.0
  SysFS BusID: 3-4:1.0
  Hardware Class: bluetooth
  Model: "Broadcom Bluetooth Device"
  Hotplug: USB
  Vendor: usb 0x0a5c "Broadcom Corp."
  Device: usb 0x217f "Broadcom Bluetooth Device"
  Revision: "7.48"
  Serial ID: "CCAF78ED1915"
  Driver: "btusb"
  Driver Modules: "btusb"
  Speed: 12 Mbps
  Module Alias: "usb:v0A5Cp217Fd0748dcE0dsc01dp01icE0isc01ip01"
  Driver Info #0:
    Driver Status: btusb is active
    Driver Activation Cmd: "modprobe btusb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #47 (Hub)

That doesn't seem to relay any info about the Bluetooth **version**, however...

Ideas anyone? I'm simply curious. Some folks just like to know what's under the hood.

---

