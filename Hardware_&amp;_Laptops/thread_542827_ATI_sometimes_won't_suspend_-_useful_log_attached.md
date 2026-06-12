---
title: "ATI sometimes won't suspend - useful log attached"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by jsully1 on 2007-09-04
Hi all,

Once every so often my Thinkpad T60 won't suspend.  I do not have issues resuming, just suspending.  Attached is some useful output in kern.log:

```

Sep  4 09:50:36 sullyslaptop kernel: [225326.256000] [fglrx:firegl_pm_save_framebuffer] *ERROR* Failed to allocate 1320 KB for saving frame buffer object.
Sep  4 09:50:36 sullyslaptop kernel: [225326.256000] [fglrx:firegl_pm_save_framebuffer] *ERROR* Failed to allocate 432 KB for saving frame buffer object.
Sep  4 09:50:36 sullyslaptop kernel: [225326.256000] [fglrx:firegl_pm_save_framebuffer] *ERROR* Failed to allocate 432 KB for saving frame buffer object.
Sep  4 09:50:36 sullyslaptop kernel: [225326.260000] [fglrx:firegl_pm_save_framebuffer] *ERROR* Failed to allocate 1320 KB for saving frame buffer object.
Sep  4 09:50:36 sullyslaptop kernel: [225326.260000] [fglrx:firegl_pm_save_framebuffer] *ERROR* Failed to allocate 432 KB for saving frame buffer object.
Sep  4 09:50:36 sullyslaptop kernel: [225326.260000] [fglrx:firegl_pm_save_framebuffer] *ERROR* Failed to allocate 1320 KB for saving frame buffer object.
Sep  4 09:50:36 sullyslaptop kernel: [225326.260000] [fglrx:firegl_pm_save_framebuffer] *ERROR* Failed to allocate 432 KB for saving frame buffer object.
Sep  4 09:50:36 sullyslaptop last message repeated 4 times
Sep  4 09:50:36 sullyslaptop kernel: [225326.260000] [fglrx:firegl_pm_save_framebuffer] *ERROR* Failed to allocate 5808 KB for saving frame buffer object.
Sep  4 09:50:36 sullyslaptop kernel: [225326.260000] [fglrx:firegl_pm_save_framebuffer] *ERROR* Failed to allocate 180 KB for saving frame buffer object.
Sep  4 09:50:36 sullyslaptop kernel: [225326.260000] [fglrx:firegl_pm_save_framebuffer] *ERROR* Failed to allocate 176 KB for saving frame buffer object.
Sep  4 09:50:36 sullyslaptop kernel: [225326.264000] [fglrx:firegl_pm_save_framebuffer] *ERROR* Failed to allocate 176 KB for saving frame buffer object.
Sep  4 09:50:36 sullyslaptop kernel: [225326.264000] [fglrx:firegl_pm_save_framebuffer] *ERROR* Failed to allocate 5808 KB for saving frame buffer object.
Sep  4 09:50:36 sullyslaptop kernel: [225326.264000] [fglrx] firegl_gps_setpowerdown .
Sep  4 09:50:36 sullyslaptop kernel: [225326.264000] [fglrx:MCIL_AllocateMemory] *ERROR* MCIL_AllocateMemory system memory failed.
Sep  4 09:50:36 sullyslaptop kernel: [225326.264000] [fglrx:firegl_gps_SetPowerState] *ERROR* Gps set power down failed.
Sep  4 09:50:36 sullyslaptop kernel: [225326.264000] [fglrx] firegl_gps_setpowerup .
Sep  4 09:50:36 sullyslaptop kernel: [225326.288000] pci_device_suspend(): fglrx_pci_suspend+0x0/0xc0 [fglrx]() returns -5
Sep  4 09:50:36 sullyslaptop kernel: [225326.288000] suspend_device(): pci_device_suspend+0x0/0x60() returns -5
Sep  4 09:50:36 sullyslaptop kernel: [225326.288000] Could not suspend device 0000:01:00.0: error -5
Sep  4 09:50:36 sullyslaptop kernel: [225326.288000] pci 0000:02:00.0: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.288000] pci 0000:03:00.0: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.288000] yenta_cardbus 0000:15:00.0: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] system 00:00: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pnp 00:01: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] system 00:02: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pnp 00:03: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pnp 00:04: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pnp 00:05: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pnp 00:06: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pnp 00:07: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] i8042 kbd 00:08: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pnp: Device 00:08 does not support activation.
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] i8042 aux 00:09: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pnp: Device 00:09 does not support activation.
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] nsc-ircc 00:0a: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pnp: Device 00:0a activated.
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pnp 00:0b: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pcspkr pcspkr: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pci_express 0000:00:01.0:pcie00: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pci_express 0000:00:1c.0:pcie00: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pci_express 0000:00:1c.0:pcie02: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pci_express 0000:00:1c.1:pcie00: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pci_express 0000:00:1c.1:pcie02: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pci_express 0000:00:1c.2:pcie00: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pci_express 0000:00:1c.2:pcie02: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pci_express 0000:00:1c.3:pcie00: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] pci_express 0000:00:1c.3:pcie02: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] serial8250 serial8250: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.292000] i8042 i8042: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.296000] atkbd serio0: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.304000] platform eisa.0: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.304000] psmouse serio1: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000] vesafb vesafb.0: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000]  usbdev1.1_ep00: PM: resume from 0, parent usb1 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000]  usbdev1.1_ep81: PM: resume from 0, parent 1-0:1.0 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000]  usbdev2.1_ep00: PM: resume from 0, parent usb2 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000]  usbdev2.1_ep81: PM: resume from 0, parent 2-0:1.0 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000]  usbdev3.1_ep00: PM: resume from 0, parent usb3 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000]  usbdev3.1_ep81: PM: resume from 0, parent 3-0:1.0 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000]  usbdev4.1_ep00: PM: resume from 0, parent usb4 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000]  usbdev4.1_ep81: PM: resume from 0, parent 4-0:1.0 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000] sd 0:0:0:0: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000]  usbdev5.1_ep00: PM: resume from 0, parent usb5 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000]  usbdev5.1_ep81: PM: resume from 0, parent 5-0:1.0 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000] sr 4:0:0:0: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000] ata5: soft resetting port
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000] platform bluetooth: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225326.924000] psmouse serio2: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225327.408000] ata5.00: configured for UDMA/33
Sep  4 09:50:36 sullyslaptop kernel: [225327.408000] ata5: EH complete
Sep  4 09:50:36 sullyslaptop kernel: [225327.436000] ata1: waiting for device to spin up (8 secs)
Sep  4 09:50:36 sullyslaptop kernel: [225329.832000] iTCO_wdt iTCO_wdt: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225329.832000] nsc-ircc nsc-ircc.0: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225329.832000] platform dock.0: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225329.832000] usb 4-1: PM: resume from 2, parent usb4 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225329.832000] usb 4-1: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225329.920000] hci_usb 4-1:1.0: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225329.920000] hci_usb 4-1:1.1: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225329.920000] usb 4-1:1.2: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225329.920000]  usbdev4.12_ep84: PM: resume from 0, parent 4-1:1.2 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225329.920000]  usbdev4.12_ep04: PM: resume from 0, parent 4-1:1.2 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225329.920000] usb 4-1:1.3: resuming
Sep  4 09:50:36 sullyslaptop kernel: [225329.920000]  usbdev4.13_ep00: PM: resume from 0, parent 4-2 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225329.920000]  usbdev4.13_ep81: PM: resume from 0, parent 4-2:1.0 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225329.920000]  usbdev4.13_ep02: PM: resume from 0, parent 4-2:1.0 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225329.920000]  usbdev4.13_ep83: PM: resume from 0, parent 4-2:1.0 still 2
Sep  4 09:50:36 sullyslaptop kernel: [225329.920000] Some devices failed to suspend

```

Any thoughts before I go play with /etc/default/acpi-support?

---

