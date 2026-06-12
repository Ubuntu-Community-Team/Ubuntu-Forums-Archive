---
title: "Cant format usb flash drive."
date: 2006-04-24
forum: Hardware &amp; Laptops
---

### Post by savas on 2006-04-24
Hi friends. I have an 64MB usb flash drive. When i try to mount it, I'm getting this message.

$ sudo mount /dev/sda /mnt/iso/ -t vfat 
mount: No medium found

I know i should use /dev/sda1 instead of /dev/sda. But kernel don't creates this device file. dmesg gives this, 

[4303164.104000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[4303164.922000] Initializing USB Mass Storage driver...
[4303164.932000] scsi0 : SCSI emulation for USB Mass Storage devices
[4303164.934000] usb-storage: device found at 2
[4303164.934000] usb-storage: waiting for device to settle before scanning
[4303164.934000] usbcore: registered new driver usb-storage
[4303164.934000] USB Mass Storage support registered.
[4303169.939000]   Vendor: Generic   Model: USB Flash Disk    Rev: 7.77
[4303169.939000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4303169.950000] usb-storage: device scan complete
[4303170.148000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0

I cant run fdisk on this disk and i cant even format it. When i try to use it under windows xp it says "no medium found" again. Similarly, I cant format it under windows and i can't repartition using xp administration tool or apps like killdisk, HP usb disk format tool vs. Is this drive dead? Sorry for bad english! Thanks for help.

---

### Post by yager on 2006-05-08
Since both operating systems can not work with this device, it appears that you either have a bad USB port or a bad drive.  Test the drive on someone elses computer to determine if it is the port on your computer or the drive itself.

---

