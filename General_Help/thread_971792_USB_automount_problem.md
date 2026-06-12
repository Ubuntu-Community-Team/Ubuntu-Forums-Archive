---
title: "USB automount problem"
date: 2008-11-05
forum: General Help
---

### Post by gvillaran on 2008-11-05
hi, until last night i noticed that my usb device was automounting fine, i updated the kernel in kubuntu and now the drive is not showing in my screen.

normally when i plugged in the usb device it showed the icon in the screen to access it, now is not working.

anyone know whats happening?

Thanks

---

### Post by gvillaran on 2008-11-05
looking at the messages :

Nov  5 11:02:37 Thor kernel: [ 5073.512327] usb 4-1: USB disconnect, address 4
Nov  5 11:02:48 Thor kernel: [ 5084.448109] usb 4-1: new high speed USB device using ehci_hcd and address 5
Nov  5 11:02:48 Thor kernel: [ 5084.585577] usb 4-1: configuration #1 chosen from 1 choice
Nov  5 11:02:48 Thor kernel: [ 5084.674380] Initializing USB Mass Storage driver...
Nov  5 11:02:48 Thor kernel: [ 5084.677190] scsi8 : SCSI emulation for USB Mass Storage devices
Nov  5 11:02:48 Thor kernel: [ 5084.680260] usbcore: registered new interface driver usb-storage
Nov  5 11:02:48 Thor kernel: [ 5084.682277] USB Mass Storage support registered.
Nov  5 11:02:48 Thor kernel: [ 5084.687354] usbcore: deregistering interface driver usb-storage
Nov  5 11:02:48 Thor kernel: [ 5084.690281] usb-storage: device found at 5
Nov  5 11:02:48 Thor kernel: [ 5084.690299] usb-storage: waiting for device to settle before scanning

it seems it not complete the mount? any ideas?

Thanks

---

### Post by gvillaran on 2008-11-05
Nov  5 11:48:55 Thor kernel: [  370.824099] usb 7-3: new high speed USB device using ehci_hcd and address 3
Nov  5 11:48:55 Thor kernel: [  370.961729] usb 7-3: configuration #1 chosen from 1 choice
Nov  5 11:48:55 Thor kernel: [  371.007638] Initializing USB Mass Storage driver...
Nov  5 11:48:55 Thor kernel: [  371.040092] scsi6 : SCSI emulation for USB Mass Storage devices
Nov  5 11:48:55 Thor kernel: [  371.046494] usb-storage: device found at 3
Nov  5 11:48:55 Thor kernel: [  371.046502] usb-storage: waiting for device to settle before scanning
Nov  5 11:48:55 Thor kernel: [  371.047556] usbcore: registered new interface driver usb-storage
Nov  5 11:48:56 Thor kernel: [  371.068881] USB Mass Storage support registered.
Nov  5 11:48:56 Thor kernel: [  371.099040] usbcore: deregistering interface driver usb-storage
Nov  5 11:48:56 Thor pulseaudio[8205]: module-hal-detect.c: Error getting capability: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_951_1602_5B75060006E0_if0_scsi_host

forgot the last line, there is the error, anyone know how can i correct it?

Thanks

---

