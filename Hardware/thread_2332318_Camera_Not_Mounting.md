---
title: "Camera Not Mounting"
date: 2016-07-30
forum: Hardware
---

### Post by Gotit on 2016-07-30
Hi,
I'm having a problem getting my external camera to mount via USB.  It worked fine in 12.04 & 14.04 but I can't get it to mount in 16.04.  The camera is recognized as a usb device: 
```
lsusb -v
Bus 002 Device 008: ID 04da:2372 Panasonic (Matsushita) Lumix Camera (Storage mode)
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04da Panasonic (Matsushita)
  idProduct          0x2372 Lumix Camera (Storage mode)
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
```

kernal log shows this:
```
Jul 30 13:08:47 Desktop kernel: [127346.876603] usb 2-2: new high-speed USB device number 7 using ehci-pci
Jul 30 13:08:47 Desktop kernel: [127347.011861] usb 2-2: New USB device found, idVendor=04da, idProduct=2372
Jul 30 13:08:47 Desktop kernel: [127347.011874] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul 30 13:08:47 Desktop kernel: [127347.011881] usb 2-2: Product: DMC-ZS15
Jul 30 13:08:47 Desktop kernel: [127347.011887] usb 2-2: Manufacturer: Panasonic
Jul 30 13:08:47 Desktop kernel: [127347.011892] usb 2-2: SerialNumber: 0000000000000000000F1202080226
Jul 30 13:08:47 Desktop kernel: [127347.013339] usb-storage 2-2:1.0: USB Mass Storage device detected
Jul 30 13:08:47 Desktop kernel: [127347.016074] usb-storage 2-2:1.0: Quirks match for vid 04da pid 2372: 90
Jul 30 13:08:47 Desktop kernel: [127347.016259] scsi host10: usb-storage 2-2:1.0
Jul 30 13:08:47 Desktop kernel: [127347.016723] usb 2-2: USB disconnect, device number 7
Jul 30 13:08:53 Desktop kernel: [127353.057910] usb 2-2: new high-speed USB device number 8 using ehci-pci
Jul 30 13:08:53 Desktop kernel: [127353.192318] usb 2-2: New USB device found, idVendor=04da, idProduct=2372
Jul 30 13:08:53 Desktop kernel: [127353.192331] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul 30 13:08:53 Desktop kernel: [127353.192338] usb 2-2: Product: DMC-ZS15
Jul 30 13:08:53 Desktop kernel: [127353.192344] usb 2-2: Manufacturer: Panasonic
Jul 30 13:08:53 Desktop kernel: [127353.192349] usb 2-2: SerialNumber: 0000000000000000000F1202080226
Jul 30 13:08:53 Desktop kernel: [127353.193746] usb-storage 2-2:1.0: USB Mass Storage device detected
Jul 30 13:08:53 Desktop kernel: [127353.197369] usb-storage 2-2:1.0: Quirks match for vid 04da pid 2372: 90
Jul 30 13:08:53 Desktop kernel: [127353.197562] scsi host11: usb-storage 2-2:1.0
Jul 30 13:08:54 Desktop kernel: [127354.198331] scsi 11:0:0:0: Direct-Access     MATSHITA DMC-ZS15         0100 PQ: 0 ANSI: 5
Jul 30 13:08:54 Desktop kernel: [127354.199568] sd 11:0:0:0: Attached scsi generic sg9 type 0
Jul 30 13:08:54 Desktop kernel: [127354.220106] sd 11:0:0:0: [sdi] Adjusting the sector count from its reported value: 31504384
Jul 30 13:08:54 Desktop kernel: [127354.220116] sd 11:0:0:0: [sdi] 31504383 512-byte logical blocks: (16.1 GB/15.0 GiB)
Jul 30 13:08:54 Desktop kernel: [127354.239058] sd 11:0:0:0: [sdi] Write Protect is off
Jul 30 13:08:54 Desktop kernel: [127354.239066] sd 11:0:0:0: [sdi] Mode Sense: 23 00 00 00
Jul 30 13:08:54 Desktop kernel: [127354.259407] sd 11:0:0:0: [sdi] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA
Jul 30 13:08:54 Desktop kernel: [127354.263123] sd 11:0:0:0: [sdi] Adjusting the sector count from its reported value: 31504384
Jul 30 13:08:54 Desktop kernel: [127354.424569]  sdi: sdi1
Jul 30 13:08:54 Desktop kernel: [127354.424587] sdi: p1 size 31496192 extends beyond EOD, enabling native capacity
Jul 30 13:08:54 Desktop kernel: [127354.426944] sd 11:0:0:0: [sdi] Adjusting the sector count from its reported value: 31504384
Jul 30 13:08:54 Desktop kernel: [127354.475541]  sdi: sdi1
Jul 30 13:08:54 Desktop kernel: [127354.475556] sdi: p1 size 31496192 extends beyond EOD, truncated
Jul 30 13:08:54 Desktop kernel: [127354.478923] sd 11:0:0:0: [sdi] Adjusting the sector count from its reported value: 31504384
Jul 30 13:08:55 Desktop kernel: [127354.520477] sd 11:0:0:0: [sdi] Attached SCSI removable disk
Jul 30 13:08:55 Desktop kernel: [127355.002463] sd 11:0:0:0: [sdi] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 30 13:08:55 Desktop kernel: [127355.002479] sd 11:0:0:0: [sdi] tag#0 Sense Key : Medium Error [current] 
Jul 30 13:08:55 Desktop kernel: [127355.002489] sd 11:0:0:0: [sdi] tag#0 Add. Sense: Unrecovered read error
Jul 30 13:08:55 Desktop kernel: [127355.002503] sd 11:0:0:0: [sdi] tag#0 CDB: Read(10) 28 00 01 e0 b7 f0 00 00 07 00
Jul 30 13:08:55 Desktop kernel: [127355.002511] blk_update_request: critical medium error, dev sdi, sector 31504368
Jul 30 13:08:55 Desktop kernel: [127355.113171] sd 11:0:0:0: [sdi] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 30 13:08:55 Desktop kernel: [127355.113188] sd 11:0:0:0: [sdi] tag#0 Sense Key : Medium Error [current] 
Jul 30 13:08:55 Desktop kernel: [127355.113197] sd 11:0:0:0: [sdi] tag#0 Add. Sense: Unrecovered read error
Jul 30 13:08:55 Desktop kernel: [127355.113207] sd 11:0:0:0: [sdi] tag#0 CDB: Read(10) 28 00 01 e0 b7 f2 00 00 05 00
Jul 30 13:08:55 Desktop kernel: [127355.113214] blk_update_request: critical medium error, dev sdi, sector 31504370
Jul 30 13:08:55 Desktop kernel: [127355.113224] Buffer I/O error on dev sdi1, logical block 31496178, async page read
Jul 30 13:08:55 Desktop kernel: [127355.113235] Buffer I/O error on dev sdi1, logical block 31496179, async page read
Jul 30 13:08:55 Desktop kernel: [127355.113241] Buffer I/O error on dev sdi1, logical block 31496180, async page read
Jul 30 13:08:55 Desktop kernel: [127355.113246] Buffer I/O error on dev sdi1, logical block 31496181, async page read
Jul 30 13:08:55 Desktop kernel: [127355.113251] Buffer I/O error on dev sdi1, logical block 31496182, async page read
Jul 30 13:08:55 Desktop kernel: [127355.113256] Buffer I/O error on dev sdi1, logical block 31496183, async page read
```

I have installed: 
```
gphoto2
gthumb
```

But the camera never mounts.  If I remove the card (PITA since there's a mounting bracket over the access) and plug it into my card reader all works as expected.

Any ideas on what could be missing??
Thanks!

---

### Post by Gotit on 2016-08-06
Bump
Am I really the only one with this problem??

---

### Post by howefield on 2016-08-06
Thread moved to the "*Hardware*" forum.

Feel free to bump your thread more often than weekly, once a day is good.

---

### Post by Gotit on 2016-08-13
Bump, again.

---

### Post by izznogooood on 2016-08-13
Try installing exfat-utils

> sudo apt install exfat-utils

---

### Post by Gotit on 2016-08-13
Thanks, izznogooood, but still no joy. :(
Any other suggestions??

---

### Post by izznogooood on 2016-08-14
Is there not any way to remove the memory card? (You can buy cheap readers on ebay).
If it worked before it may be the driver was dropped from the Kernel. Do you know anything about installing a custom kernel? (Or search for a module).

Can you input your exact model and name of the Camera?

---

### Post by Gotit on 2016-08-27
Hi izznogooood,

The camera is
```
Product: Lumix DMC-ZS15
Manufacturer: Panasonic
```

No experience with custom kernels, unless installing drivers/modules counts as a custom kernel.
I would check to see if the camera is still included, but I can't figure out "what" to research.

I have an external card reader, but getting the card out is a PITA as I have a mounting bracket over the card door.

It just seems so odd that it's recognized as a usb device when I plug it in, but it's ignored in nautilus/unity.

Does this work for anyone out there??

---

### Post by Gotit on 2016-11-18
OK, since I seem to be the only one with this issue, I decided to create a manual work around.
Since I see the camera attach to /dev/sdi1 when I plug it into the usb port, I use pmount to create a user owned mount point for it in /media.  Then I launch gthumb and call the import dialog.  Lastly, I cerated a desktop button for this in unity and put it in /home/gotit/.local/share/applications.

camera_mount script:
```
#!/bin/sh
if mountpoint -q /media/camera
	then pumount camera
	else pmount /dev/sdi1/ camera 
		sleep 1 
		gthumb --import-photos
fi
```

Desktop button:
```
[Desktop Entry]
Type=Application
Name=Camera Mount
Exec=/home/gotit/Scripts/camera_mount.sh
Keywords=camera,photos
Icon=/home/gotit/Icons/Camera.png
Categories=Unity;Media;
```

If anyone has a better method, please chime in.

---

