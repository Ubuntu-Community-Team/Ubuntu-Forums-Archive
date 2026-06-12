---
title: "Motorokr w5"
date: 2009-05-18
forum: Hardware
---

### Post by B4RR13N705 on 2009-05-18
Hi, i have a Motorokr W5 and i want to plug it to my Ubuntu Desktop running Hardy.
I plug my phone, i check "lsusb", and i can see my phone there. But the phone doesnt mount. Sometimes it mounts alone, but other days im unlucky and my cell phone does not mount.
I checked dmesg and got this:
```

[ 5872.679434] usb 2-4: new full speed USB device using ohci_hcd and address 3
[ 5872.874104] usb 2-4: configuration #1 chosen from 1 choice
[ 5872.881159] scsi8 : SCSI emulation for USB Mass Storage devices
[ 5872.881638] usb-storage: device found at 3
[ 5872.881843] usb-storage: waiting for device to settle before scanning
[ 5877.873134] usb-storage: device scan complete
[ 5883.517180] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[ 5893.834177] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[ 5894.179342] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[ 5904.494347] usb 2-4: reset full speed USB device using ohci_hcd and address 3
[ 5904.679033] scsi 8:0:0:0: Device offlined - not ready after error recovery

```
Does anybody have the same problem?

---

