---
title: "flash drive visible in disks but not in files"
date: 2023-02-15
forum: Hardware
---

### Post by cmacc77 on 2023-02-15
i've formatted the usb stick but it won't show up in files, but shows up in disks.  I've tried quick and full format and all 3 format options.  any suggestions?

---

### Post by #&amp;thj^% on 2023-02-15
In some cases&#8212;such as if you're using a laptop&#8212;power issues might be affecting its ability to detect USB devices. The autosuspend setting is designed to reduce power usage on Linux laptops, but it can prove counterproductive.
show us this please:
```
lsusb
```
and:
```
sudo dmesg | grep -i USB

```

---

### Post by cmacc77 on 2023-02-15
thanks for the assistance.  i rebooted and the drive still isn't showing up.  not sure if that eliminates the autosuspend as a possible cause, and im using a desktop.

~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:e009 Qualcomm Atheros Communications 
Bus 001 Device 005: ID 046d:08e3 Logitech, Inc. C505 HD Webcam
Bus 001 Device 004: ID 062a:4c01 MosArt Semiconductor Corp. 2,4Ghz Wireless Transceiver [for Delux M618 Plus Wireless Vertical Mouse]
Bus 001 Device 006: ID 1235:8211 Focusrite-Novation Scarlett Solo (3rd Gen.)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and

:~$ sudo dmesg | grep -i USB
[sudo] password for : 
[    0.240465] ACPI: bus type USB registered
[    0.240465] usbcore: registered new interface driver usbfs
[    0.240465] usbcore: registered new interface driver hub
[    0.240465] usbcore: registered new device driver usb
[    0.318389] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.318404] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.318423] uhci_hcd: USB Universal Host Controller Interface driver
[    0.770428] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.773053] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.773055] xhci_hcd 0000:00:14.0: Host supports USB 3.0 SuperSpeed
[    0.773077] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.15
[    0.773078] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.773079] usb usb1: Product: xHCI Host Controller
[    0.773080] usb usb1: Manufacturer: Linux 5.15.0-60-generic xhci-hcd
[    0.773081] usb usb1: SerialNumber: 0000:00:14.0
[    0.774122] hub 1-0:1.0: USB hub found
[    0.775365] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.15
[    0.775367] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.775368] usb usb2: Product: xHCI Host Controller
[    0.775369] usb usb2: Manufacturer: Linux 5.15.0-60-generic xhci-hcd
[    0.775369] usb usb2: SerialNumber: 0000:00:14.0
[    0.775434] hub 2-0:1.0: USB hub found
[    0.776034] usb: port power management may be unreliable
[    0.776357] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 3
[    0.835562] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 4
[    0.835564] xhci_hcd 0000:02:00.0: Host supports USB 3.1 Enhanced SuperSpeed
[    0.835642] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.15
[    0.835644] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.835645] usb usb3: Product: xHCI Host Controller
[    0.835646] usb usb3: Manufacturer: Linux 5.15.0-60-generic xhci-hcd
[    0.835646] usb usb3: SerialNumber: 0000:02:00.0
[    0.835763] hub 3-0:1.0: USB hub found
[    0.835994] usb usb4: We don't know the algorithms for LPM for this host, disabling LPM.
[    0.836004] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.15
[    0.836005] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.836006] usb usb4: Product: xHCI Host Controller
[    0.836007] usb usb4: Manufacturer: Linux 5.15.0-60-generic xhci-hcd
[    0.836008] usb usb4: SerialNumber: 0000:02:00.0
[    0.836103] hub 4-0:1.0: USB hub found
[    1.110113] usb 2-4: new SuperSpeed USB device number 2 using xhci_hcd
[    1.135311] usb 2-4: New USB device found, idVendor=090c, idProduct=1000, bcdDevice=11.00
[    1.135321] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.135325] usb 2-4: Product: Flash Drive
[    1.135328] usb 2-4: Manufacturer: Samsung
[    1.135331] usb 2-4: SerialNumber: 0373620080001378
[    1.261914] usb 1-1: new high-speed USB device number 2 using xhci_hcd
[    1.412523] usb 1-1: New USB device found, idVendor=058f, idProduct=6366, bcdDevice= 1.00
[    1.412535] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.412541] usb 1-1: Product: Flash Card Reader/Writer
[    1.412545] usb 1-1: Manufacturer: Generic
[    1.412548] usb 1-1: SerialNumber: 058F63666485
[    1.541998] usb 1-8: new full-speed USB device number 3 using xhci_hcd
[    1.692012] usb 1-8: New USB device found, idVendor=0cf3, idProduct=e009, bcdDevice= 0.01
[    1.692023] usb 1-8: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.821988] usb 1-13: new full-speed USB device number 4 using xhci_hcd
[    1.972516] usb 1-13: New USB device found, idVendor=062a, idProduct=4c01, bcdDevice= 1.17
[    1.972528] usb 1-13: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.972532] usb 1-13: Product: 2.4G INPUT DEVICE
[    1.972536] usb 1-13: Manufacturer: MOSART Semi.
[    2.101987] usb 1-14: new high-speed USB device number 5 using xhci_hcd
[    2.481841] usb 1-14: New USB device found, idVendor=046d, idProduct=08e3, bcdDevice= 0.21
[    2.481857] usb 1-14: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[    2.481863] usb 1-14: Product: C505 HD Webcam
[    2.481867] usb 1-14: SerialNumber: 0270F420
[    2.497029] usb-storage 2-4:1.0: USB Mass Storage device detected
[    2.497264] scsi host5: usb-storage 2-4:1.0
[    2.497307] usb-storage 1-1:1.0: USB Mass Storage device detected
[    2.497469] scsi host6: usb-storage 1-1:1.0
[    2.497515] usbcore: registered new interface driver usb-storage
[    2.498354] usbcore: registered new interface driver uas
[    2.501192] usbcore: registered new interface driver usbhid
[    2.501194] usbhid: USB HID core driver
[    2.502605] input: MOSART Semi. 2.4G INPUT DEVICE as /devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.0/0003:062A:4C01.0001/input/input3
[    2.562366] hid-generic 0003:062A:4C01.0001: input,hidraw0: USB HID v1.10 Keyboard [MOSART Semi. 2.4G INPUT DEVICE] on usb-0000:00:14.0-13/input0
[    2.562984] input: MOSART Semi. 2.4G INPUT DEVICE Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.1/0003:062A:4C01.0002/input/input4
[    2.563482] input: MOSART Semi. 2.4G INPUT DEVICE Consumer Control as /devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.1/0003:062A:4C01.0002/input/input5
[    2.622290] input: MOSART Semi. 2.4G INPUT DEVICE System Control as /devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.1/0003:062A:4C01.0002/input/input6
[    2.622591] input: MOSART Semi. 2.4G INPUT DEVICE as /devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.1/0003:062A:4C01.0002/input/input7
[    2.623030] hid-generic 0003:062A:4C01.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [MOSART Semi. 2.4G INPUT DEVICE] on usb-0000:00:14.0-13/input1
[   13.464231] usbcore: registered new interface driver btusb
[   16.562109] usb 1-14: Warning! Unlikely big volume range (=6144), cval->res is probably wrong.
[   16.562121] usb 1-14: [5] FU [Mic Capture Volume] ch = 1, val = 1536/7680/1
[   16.562764] usbcore: registered new interface driver snd-usb-audio
[   16.562956] usb 1-14: Found UVC 1.00 device C505 HD Webcam (046d:08e3)
[   16.601367] input: C505 HD Webcam as /devices/pci0000:00/0000:00:14.0/usb1/1-14/1-14:1.0/input/input20
[   16.601467] usbcore: registered new interface driver uvcvideo
[   35.278425] usb 1-14: reset high-speed USB device number 5 using xhci_hcd
[ 7444.991918] usb 1-1: reset high-speed USB device number 2 using xhci_hcd
[ 7448.268921] usb 2-4: USB disconnect, device number 2
[ 7449.931746] usb 2-4: new SuperSpeed USB device number 3 using xhci_hcd
[ 7449.953045] usb 2-4: New USB device found, idVendor=090c, idProduct=1000, bcdDevice=11.00
[ 7449.953059] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 7449.953065] usb 2-4: Product: Flash Drive
[ 7449.953069] usb 2-4: Manufacturer: Samsung
[ 7449.953073] usb 2-4: SerialNumber: 0373620080001378
[ 7450.067909] usb-storage 2-4:1.0: USB Mass Storage device detected
[ 7450.068255] scsi host7: usb-storage 2-4:1.0
[ 7460.819283] usb 1-12: new high-speed USB device number 6 using xhci_hcd
[ 7460.967590] usb 1-12: New USB device found, idVendor=1235, idProduct=8211, bcdDevice= 6.45
[ 7460.967593] usb 1-12: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[ 7460.967594] usb 1-12: Product: Scarlett Solo USB
[ 7460.967595] usb 1-12: Manufacturer: Focusrite
[ 7460.967596] usb 1-12: SerialNumber: Y7HR04N13BE118
[ 7461.215556] usb 1-12: Focusrite Scarlett Gen 2/3 Mixer Driver disabled; use options snd_usb_audio vid=0x1235 pid=0x8211 device_setup=1 to enable and report any issues to [email]g@b4.vu[/email]
[ 7489.384974] usb 1-1: USB disconnect, device number 2
[ 7553.651951] usb 2-4: USB disconnect, device number 3
[ 7556.298373] usb 2-3: new SuperSpeed USB device number 4 using xhci_hcd
[ 7556.319598] usb 2-3: New USB device found, idVendor=090c, idProduct=1000, bcdDevice=11.00
[ 7556.319612] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 7556.319617] usb 2-3: Product: Flash Drive
[ 7556.319621] usb 2-3: Manufacturer: Samsung
[ 7556.319625] usb 2-3: SerialNumber: 0373620080001378
[ 7556.442812] usb-storage 2-3:1.0: USB Mass Storage device detected
[ 7556.443520] scsi host5: usb-storage 2-3:1.0

---

### Post by TheFu on 2023-02-15
> **cmacc77 said:**
> i've formatted the usb stick but it won't show up in files, but shows up in disks.  I've tried quick and full format and all 3 format options.  any suggestions?

a) always create a partition on all disks. Some tools don't work without a partition table.
b) Avoid using mounts that happen through a GUI - i.e. gvfs.  For non-native file systems, the options are far from optimal.  Use the /etc/fstab or autofs instead.

Disks (whatever that is, perhaps you mean gnome-disks?) is not the same as a file manager. It has a different purpose.  Personally, I prefer/trust 'gparted' for everything that Gnome-disks does. 

Files (really Nautilus) is a file manager.  If the storage uses a real mount, then it won't show up as a separate item to click. It will be in the file system based on where it is mounted.  You can create a bookmark to pull it out, if you like.  At least in Caja (a competing file manager) that's possible.  I think, but don't quote me, most Linux file managers have preferences/settings that control what happens when different storage is connected.  You might check those settings.  In general, I prefer the "Do Nothing" option for security reasons.  The idea that someone walking by could insert a flash drive that loads kernel drivers without my explicit approval is very concerning, but everyone needs to decide what risks they will accept.

If you watch the logs (dmesg -w) when any usb device is inserted, you will probably see if there are errors/problems.  Don't forget to wait 10 seconds between inserting or removing USB devices for the OS to see that electrical connect created/removed.  **Looks like there's no partition table in the flash drive.** I think that's the issue.  Create a partition table, then create a partition, then format the partition with the file system you like and give it a label that makes sense to you. This will determine where gvfs mount it.

Not all USB storage devices work with all USB ports.  This has become less and less a problem over the last 13 yrs.

What file systems does the flash drive have on it?
Which Ubuntu release is running?  
I ask because exFAT drivers weren't included by default in some Ubuntu releases.

---

