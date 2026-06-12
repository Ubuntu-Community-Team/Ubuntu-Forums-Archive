---
title: "Ubuntu 14.04 stopped recognizing USB 160G WD drive"
date: 2015-05-31
forum: Hardware
---

### Post by PeterOakland on 2015-05-31
Don't know what happened, but suddenly my backup external drive isn't recognized by desktop running 14.04 3.13.0-53-generic #89.
Drive is seen by a laptop running 3.16.0 -- so the drive and its cable are fine.  And the USB port on the desktop sees a flash drive with no problem.
I don't begin to know where to look or what to do, and would appreciate any possible help.
Not being able to save my /home to the external puts me at a clear disadvantage.

Thanks for any help/insight/advice.

Peter
OaklandLinux desktop

---

### Post by weatherman2 on 2015-05-31
What happens when you plug it in?  Right after you do, type these terminal commands and report back the results (or at least, the meaningful results):

```
dmesg
dmesg | grep -i usb
lsusb
ls /dev/disk/by-id

```

---

### Post by PeterOakland on 2015-06-01
dmesg - the relevant (I think) part:

[  469.388036] usb 1-5: new high-speed USB device number 4 using ehci-pci
[  533.216039] usb 1-5: new high-speed USB device number 5 using ehci-pci
[  861.575443] perf samples too long (2514 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  893.412040] usb 1-5: new high-speed USB device number 6 using ehci-pci
[  914.868059] usb 1-5: new high-speed USB device number 7 using ehci-pci
[ 1000.172064] usb 1-5: new high-speed USB device number 8 using ehci-pci
[ 1042.840056] usb 1-5: new high-speed USB device number 9 using ehci-pci
[ 1042.973083] usb 1-5: New USB device found, idVendor=1058, idProduct=0702
[ 1042.973092] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1042.973097] usb 1-5: Product: External HDD    
[ 1042.973101] usb 1-5: Manufacturer: Western Digital 
[ 1042.973105] usb 1-5: SerialNumber: D8762D42CA4F1B5FD208DAD4
[ 1043.023312] usb-storage 1-5:1.0: USB Mass Storage device detected
[ 1043.023743] scsi4 : usb-storage 1-5:1.0
[ 1043.023851] usbcore: registered new interface driver usb-storage
[ 1043.203393] usb 1-5: USB disconnect, device number 9
[ 1064.724050] usb 1-5: new high-speed USB device number 10 using ehci-pci
[ 1065.252030] usb 1-5: device not accepting address 10, error -71
[ 1128.640041] usb 1-5: new high-speed USB device number 12 using ehci-pci
[ 1129.168059] usb 1-5: device not accepting address 12, error -71


dmesg | grep -i usb:

  0.140235] ACPI: bus type USB registered
[    0.140235] usbcore: registered new interface driver usbfs
[    0.140235] usbcore: registered new interface driver hub
[    0.140235] usbcore: registered new device driver usb
[    0.555100] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.555229] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.568018] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.568113] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.568118] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.568122] usb usb1: Product: EHCI Host Controller
[    0.568126] usb usb1: Manufacturer: Linux 3.13.0-53-generic ehci_hcd
[    0.568130] usb usb1: SerialNumber: 0000:00:1d.7
[    0.568264] hub 1-0:1.0: USB hub found
[    0.568435] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.568453] uhci_hcd: USB Universal Host Controller Interface driver
[    0.568544] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.568611] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.568613] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.568615] usb usb2: Product: UHCI Host Controller
[    0.568617] usb usb2: Manufacturer: Linux 3.13.0-53-generic uhci_hcd
[    0.568619] usb usb2: SerialNumber: 0000:00:1d.0
[    0.568710] hub 2-0:1.0: USB hub found
[    0.568859] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.568923] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.568926] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.568927] usb usb3: Product: UHCI Host Controller
[    0.568929] usb usb3: Manufacturer: Linux 3.13.0-53-generic uhci_hcd
[    0.568931] usb usb3: SerialNumber: 0000:00:1d.1
[    0.569020] hub 3-0:1.0: USB hub found
[    0.569169] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.569243] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.569245] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.569247] usb usb4: Product: UHCI Host Controller
[    0.569249] usb usb4: Manufacturer: Linux 3.13.0-53-generic uhci_hcd
[    0.569250] usb usb4: SerialNumber: 0000:00:1d.2
[    0.569337] hub 4-0:1.0: USB hub found
[    0.569487] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.569559] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.569562] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.569564] usb usb5: Product: UHCI Host Controller
[    0.569565] usb usb5: Manufacturer: Linux 3.13.0-53-generic uhci_hcd
[    0.569567] usb usb5: SerialNumber: 0000:00:1d.3
[    0.569655] hub 5-0:1.0: USB hub found
[    1.248046] usb 2-2: new low-speed USB device number 2 using uhci_hcd
[    1.425052] usb 2-2: New USB device found, idVendor=046d, idProduct=c315
[    1.425059] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.425064] usb 2-2: Product: Logitech USB Keyboard
[    1.425069] usb 2-2: Manufacturer: Logitech
[    1.540048] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    1.718047] usb 3-2: New USB device found, idVendor=045e, idProduct=00f6
[    1.718054] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.718059] usb 3-2: Product: Comfort Optical Mouse 1000
[    1.718063] usb 3-2: Manufacturer: Microsoft
[   10.955408] usbcore: registered new interface driver usbhid
[   10.955412] usbhid: USB HID core driver
[   10.976001] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input11
[   10.996920] hid-generic 0003:046D:C315.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.0-2/input0
[   10.997276] input: Microsoft Comfort Optical Mouse 1000 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input12
[   11.001382] hid-generic 0003:045E:00F6.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Comfort Optical Mouse 1000] on usb-0000:00:1d.1-2/input0
[  469.388036] usb 1-5: new high-speed USB device number 4 using ehci-pci
[  533.216039] usb 1-5: new high-speed USB device number 5 using ehci-pci


lsusb: 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00f6 Microsoft Corp. Comfort Optical Mouse 1000
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c315 Logitech, Inc. Classic Keyboard 200
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ls /dev/disk/by-id:  
ata-Optiarc_DVD_RW_AD-7220A             ata-TOSHIBA_DT01ACA050_Y3GZWZVAS-part2  wwn-0x5000039ff8ce0c39        wwn-0x5000039ff8ce0c39-part5
ata-TOSHIBA_DT01ACA050_Y3GZWZVAS        ata-TOSHIBA_DT01ACA050_Y3GZWZVAS-part5  wwn-0x5000039ff8ce0c39-part1  wwn-0x5000039ff8ce0c39-part6
ata-TOSHIBA_DT01ACA050_Y3GZWZVAS-part1  ata-TOSHIBA_DT01ACA050_Y3GZWZVAS-part6  wwn-0x5000039ff8ce0c39-part2

---

### Post by PeterOakland on 2015-06-01
It's working again!  I have no idea what happened.  I tried it last night on several different usb ports, and none of them worked.
Tonight, the original one I had been using, on the lower front of the box, connected to the MB by a wire, still doesn't recognize it.
But the one on the back, on a hub directly soldered to the MB, the port that didn't work last night now works.
Thanks for the reply and suggestions, and now, I guess, all that stuff is moot.

Peter
Oakland

---

