---
title: "Ubuntu crashes when smart card is removed..."
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by Izek on 2008-02-08
As the title says, when I remove my Belkin G+ MIMO Wireless card from my smart card slot, Ubuntu will freeze and not respond to anything, forcing me to manually shutdown using the power button.

---

### Post by alastair on 2008-02-08
> **Izek said:**
> As the title says, when I remove my Belkin G+ MIMO Wireless card from my smart card slot, Ubuntu will freeze and not respond to anything, forcing me to manually shutdown using the power button.

Wait a minute or so, before reset.

Then, back in and have a look at the logs :

/var/log/syslog

Any errors or warnings printed - about the time of the freeze?

Alastair

---

### Post by Izek on 2008-02-08
> **alastair said:**
> Wait a minute or so, before reset.

Then, back in and have a look at the logs :

/var/log/syslog

Any errors or warnings printed - about the time of the freeze?

Alastair

The normal syslog says...

```
Feb  8 08:31:07 izek-laptop python: io/hpmud/jd.c 84: unable to read device-id 
Feb  8 08:31:07 izek-laptop python: hp-makeuri[6299]: error: Error: Unknown/invalid device-uri field
Feb  8 08:31:07 izek-laptop python: hp-makeuri[6299]: error: Device not found
Feb  8 08:31:10 izek-laptop python: io/hpmud/jd.c 84: unable to read device-id 
Feb  8 08:31:10 izek-laptop python: hp-makeuri[6301]: error: Error: Unknown/invalid device-uri field
Feb  8 08:31:10 izek-laptop python: hp-makeuri[6301]: error: Device not found
Feb  8 08:31:19 izek-laptop python: io/hpmud/jd.c 84: unable to read device-id 
Feb  8 08:31:19 izek-laptop python: hp-makeuri[6316]: error: Error: Unknown/invalid device-uri field
Feb  8 08:31:19 izek-laptop python: hp-makeuri[6316]: error: Device not found
Feb  8 08:31:49 izek-laptop python: io/hpmud/jd.c 84: unable to read device-id 
Feb  8 08:31:49 izek-laptop python: hp-makeuri[6346]: error: Error: Unknown/invalid device-uri field
Feb  8 08:31:49 izek-laptop python: hp-makeuri[6346]: error: Device not found
Feb  8 08:31:52 izek-laptop kernel: [  605.964000] usb 5-2: new high speed USB device using ehci_hcd and address 5
Feb  8 08:31:52 izek-laptop kernel: [  606.096000] usb 5-2: configuration #1 chosen from 1 choice
Feb  8 08:31:52 izek-laptop kernel: [  606.096000] scsi7 : SCSI emulation for USB Mass Storage devices
Feb  8 08:31:52 izek-laptop NetworkManager: <debug> [1202481112.781010] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_5406_00001673A6701DD9'). 
Feb  8 08:31:52 izek-laptop kernel: [  606.096000] usb-storage: device found at 5
Feb  8 08:31:52 izek-laptop kernel: [  606.096000] usb-storage: waiting for device to settle before scanning
Feb  8 08:31:52 izek-laptop NetworkManager: <debug> [1202481112.853910] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_5406_00001673A6701DD9_if0'). 
Feb  8 08:31:52 izek-laptop NetworkManager: <debug> [1202481112.855181] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_5406_00001673A6701DD9_usbraw'). 
Feb  8 08:31:53 izek-laptop python: io/hpmud/jd.c 84: unable to read device-id 
Feb  8 08:31:53 izek-laptop python: hp-makeuri[6348]: error: Error: Unknown/invalid device-uri field
Feb  8 08:31:53 izek-laptop python: hp-makeuri[6348]: error: Device not found
```

syslog.0 doesn't have any of this.

---

