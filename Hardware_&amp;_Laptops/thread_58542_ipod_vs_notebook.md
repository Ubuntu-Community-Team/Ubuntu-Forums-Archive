---
title: "ipod vs notebook"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by Zelut on 2005-08-20
I've got my iPod plugged into my notebook but it doesn't seem to mount or see the files listed.  Can anyone give me any pointers?  I've installed gtkpod-aac and dmesg shows a connection w/o errors.  I do not see the ipod under /dev/sd* or /media/

new high speed USB device using ehci_hcd and address 2
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.63
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete
SCSI device sda: 39063023 512-byte hdwr sectors (20000 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
SCSI device sda: 39063023 512-byte hdwr sectors (20000 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1 p2
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0

any help is appreciated.  4th gen, 20G ipod...

---

### Post by s_p_a_r_k_y on 2005-08-20
have you tried manually mounting it? 
```
 sudo mount /dev/sdaX 
```

to find out which partition to use, try ```
sudo cfdisk /dev/sda 
```
and it should tell you whihc partition is the music one...there is a OS partition which should be sda1, so I'm assuming sda2 is music...but then again I put linux on my ipod so I have a different partition table...don't ask why I put it on (ok I did it to play pong)

---

