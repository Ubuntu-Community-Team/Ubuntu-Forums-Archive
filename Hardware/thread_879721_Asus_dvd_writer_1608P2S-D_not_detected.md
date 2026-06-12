---
title: "Asus dvd writer 1608P2S-D not detected"
date: 2008-08-04
forum: Hardware
---

### Post by The Dragon Master on 2008-08-04
Hi, I have an Asus DRW 1608P2S-D connected via USB 2 which is not being detected.

dave@daves-desktop:~$ tail -n 20 /var/log/kern.log
Aug  4 16:20:30 daves-desktop kernel: [  784.993752] usb 4-4: USB disconnect, address 65
Aug  4 16:20:30 daves-desktop kernel: [  785.266334] usb 4-4: new high speed USB device using ehci_hcd and address 66
Aug  4 16:20:30 daves-desktop kernel: [  785.505480] usb 4-4: configuration #1 chosen from 1 choice
Aug  4 16:20:30 daves-desktop kernel: [  785.535441] scsi47 : SCSI emulation for USB Mass Storage devices
Aug  4 16:20:30 daves-desktop kernel: [  785.542428] usb-storage: device found at 66
Aug  4 16:20:30 daves-desktop kernel: [  785.542435] usb-storage: waiting for device to settle before scanning
Aug  4 16:20:31 daves-desktop kernel: [  785.932462] usb 4-4: USB disconnect, address 66
Aug  4 16:20:31 daves-desktop kernel: [  786.170074] usb 4-4: new high speed USB device using ehci_hcd and address 67
Aug  4 16:20:31 daves-desktop kernel: [  786.409247] usb 4-4: configuration #1 chosen from 1 choice
Aug  4 16:20:31 daves-desktop kernel: [  786.439195] scsi48 : SCSI emulation for USB Mass Storage devices
Aug  4 16:20:31 daves-desktop kernel: [  786.446176] usb-storage: device found at 67
Aug  4 16:20:31 daves-desktop kernel: [  786.446183] usb-storage: waiting for device to settle before scanning
Aug  4 16:20:32 daves-desktop kernel: [  786.839081] usb 4-4: USB disconnect, address 67
Aug  4 16:20:32 daves-desktop kernel: [  787.077826] usb 4-4: new high speed USB device using ehci_hcd and address 68
Aug  4 16:20:32 daves-desktop kernel: [  787.321145] usb 4-4: configuration #1 chosen from 1 choice
Aug  4 16:20:32 daves-desktop kernel: [  787.356941] scsi49 : SCSI emulation for USB Mass Storage devices
Aug  4 16:20:32 daves-desktop kernel: [  787.369403] usb-storage: device found at 68
Aug  4 16:20:32 daves-desktop kernel: [  787.369410] usb-storage: waiting for device to settle before scanning
Aug  4 16:20:33 daves-desktop kernel: [  788.434409] usb 4-4: USB disconnect, address 68
Aug  4 16:20:34 daves-desktop kernel: [  788.705388] usb 4-4: new high speed USB device using ehci_hcd and address 69

any ideas? :confused:

---

### Post by The Dragon Master on 2008-08-04
Here is the last part of the output from 

$ dmesg
[  784.575512] scsi46 : SCSI emulation for USB Mass Storage devices
[  784.582690] usb-storage: device found at 65
[  784.582697] usb-storage: waiting for device to settle before scanning
[  784.993752] usb 4-4: USB disconnect, address 65
[  785.266334] usb 4-4: new high speed USB device using ehci_hcd and address 66
[  785.505480] usb 4-4: configuration #1 chosen from 1 choice
[  785.535441] scsi47 : SCSI emulation for USB Mass Storage devices
[  785.542428] usb-storage: device found at 66
[  785.542435] usb-storage: waiting for device to settle before scanning
[  785.932462] usb 4-4: USB disconnect, address 66
[  786.170074] usb 4-4: new high speed USB device using ehci_hcd and address 67
[  786.409247] usb 4-4: configuration #1 chosen from 1 choice
[  786.439195] scsi48 : SCSI emulation for USB Mass Storage devices
[  786.446176] usb-storage: device found at 67
[  786.446183] usb-storage: waiting for device to settle before scanning
[  786.839081] usb 4-4: USB disconnect, address 67
[  787.077826] usb 4-4: new high speed USB device using ehci_hcd and address 68
[  787.321145] usb 4-4: configuration #1 chosen from 1 choice
[  787.356941] scsi49 : SCSI emulation for USB Mass Storage devices
[  787.369403] usb-storage: device found at 68
[  787.369410] usb-storage: waiting for device to settle before scanning
[  788.434409] usb 4-4: USB disconnect, address 68
[  788.705388] usb 4-4: new high speed USB device using ehci_hcd and address 69

:confused:

---

### Post by The Dragon Master on 2008-08-04
the following one-liner has solved the problem, is anyone able to explain why?

sudo modprobe -r ehci-hcd

---

### Post by The Dragon Master on 2008-08-05
It seems I must run this line again each time I turn the computer on. Is there a hack to avoid doing this manually every time I turn the computer on?

Thanks
TDM

---

