---
title: "USB 3TB HDD will not partition or mount (hangs)"
date: 2011-10-21
forum: Hardware
---

### Post by sdetheridge on 2011-10-21
I've been pulling my hair out with this one most of the day...

I have three IcyBox IB-351 series (IB-351StU3-B) external USB SATA enclosures. Two contain 3TB drives, one contains a 750G one.

When I connect a 3TB external drive to a machine running Ubuntu Server 10.04.3 and try to access it, it hangs completely. For example, running parted, mounting a partition, or running badblocks. It just hangs and I usually have to kill -9 the process.

I know the enclosure works with 3TB drives, as I can hook the device up to a Windows PC, create a 3TB partition, mount it and use it just fine. I also know the enclosure works with Linux, as the one running a 750G drive works just fine as well. I know it's not a problem with my specific USB controller, as I have hooked the drive up to a different Ubuntu server with different hardware, with the same results. All above operating systems are 64-bit.

The machines are perfectly capable of working with 3TB internal drives.

I have tried swapping drives and cables, to ensure I hadn't got 2 faulty ones. Same results.

Here is what dmesg says when I connect and attempt to use the device:

```

[685772.270020] usb 1-4: new high speed USB device using ehci_hcd and address 6
[685772.426961] usb 1-4: configuration #1 chosen from 1 choice
[685772.427386] scsi4 : SCSI emulation for USB Mass Storage devices
[685772.427509] usb-storage: device found at 6
[685772.427514] usb-storage: waiting for device to settle before scanning
[685777.421648] usb-storage: device scan complete
[685781.621724] scsi 4:0:0:0: Direct-Access     WDC WD30 EZRX-00MMMB0     80.0 PQ: 0 ANSI: 2
[685781.622341] sd 4:0:0:0: Attached scsi generic sg3 type 0
[685781.626581] sd 4:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[685781.627079] sd 4:0:0:0: [sdc] 5860533165 512-byte logical blocks: (3.00 TB/2.72 TiB)
[685781.627827] sd 4:0:0:0: [sdc] Write Protect is off
[685781.627831] sd 4:0:0:0: [sdc] Mode Sense: 00 06 00 00
[685781.627834] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[685781.632076] sd 4:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[685781.633201] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[685781.633450]  sdc: unknown partition table
[685781.652453] sd 4:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[685781.653577] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[685781.653828] sd 4:0:0:0: [sdc] Attached SCSI disk
[685812.071907] usb 1-4: reset high speed USB device using ehci_hcd and address 6
[685844.101896] usb 1-4: reset high speed USB device using ehci_hcd and address 6
[685876.100648] usb 1-4: reset high speed USB device using ehci_hcd and address 6
[685908.100650] usb 1-4: reset high speed USB device using ehci_hcd and address 6
[685940.101897] usb 1-4: reset high speed USB device using ehci_hcd and address 6
[685972.160666] usb 1-4: reset high speed USB device using ehci_hcd and address 6
[685973.316165] sd 4:0:0:0: [sdc] Unhandled error code
[685973.316170] sd 4:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[685973.316175] sd 4:0:0:0: [sdc] CDB: Read(16): 88 00 00 00 00 01 5d 50 a3 00 00 00
[685973.316188] end_request: I/O error, dev sdc, sector 5860532992
[685973.316440] Buffer I/O error on device sdc, logical block 5860532992
[685973.316696] Buffer I/O error on device sdc, logical block 5860532993
[685973.316948] Buffer I/O error on device sdc, logical block 5860532994
[685973.317200] Buffer I/O error on device sdc, logical block 5860532995
[685973.317453] Buffer I/O error on device sdc, logical block 5860532996
[685973.317706] Buffer I/O error on device sdc, logical block 5860532997
[685973.317957] Buffer I/O error on device sdc, logical block 5860532998
[685973.318209] Buffer I/O error on device sdc, logical block 5860532999
[686004.070646] usb 1-4: reset high speed USB device using ehci_hcd and address 6
[686036.071896] usb 1-4: reset high speed USB device using ehci_hcd and address 6
[686068.070647] usb 1-4: reset high speed USB device using ehci_hcd and address 6
[686100.070645] usb 1-4: reset high speed USB device using ehci_hcd and address 6
[686132.131625] usb 1-4: reset high speed USB device using ehci_hcd and address 6
[686164.130653] usb 1-4: reset high speed USB device using ehci_hcd and address 6
[686165.296588] sd 4:0:0:0: [sdc] Unhandled error code
[686165.296593] sd 4:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[686165.296598] sd 4:0:0:0: [sdc] CDB: Read(16): 88 00 00 00 00 01 5d 50 a3 a8 00 00
[686165.296612] end_request: I/O error, dev sdc, sector 5860533160
[686165.296863] Buffer I/O error on device sdc, logical block 5860533160
[686165.297117] Buffer I/O error on device sdc, logical block 5860533161
[686165.297370] Buffer I/O error on device sdc, logical block 5860533162
[686165.297622] Buffer I/O error on device sdc, logical block 5860533163
[686165.297874] Buffer I/O error on device sdc, logical block 5860533164

```

Note, the error about 'unknown partition table' is expected. There's no partition table on it.

lsusb says:

```


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 006: ID 1234:5678**
Bus 001 Device 005: ID 046d:c05b Logitech, Inc.
Bus 001 Device 004: ID 04f2:0116 Chicony Electronics Co., Ltd KU-2971 German Keyboard
Bus 001 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Device ID 1234:5678 seems a bit off to me, but that's how it shows up on both boxes. (One has an "unknown" after it) - This is also how it shows up when I have a working 750G drive installed, so this could well be a non-issue.

One thing that was a little odd, was that it was initially trying to load usbtouchscreen as well as usb_storage when I inserted the device. I blacklisted this module. It didn't seem to make a difference.

Here's what lsusb -v has to say about that particular device:
```

Bus 001 Device 006: ID 1234:5678
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x1234
  idProduct          0x5678
  bcdDevice            0.05
  iManufacturer           1 VLI manufacture String
  iProduct                2 VLI Product String
  iSerial                 3 0000000000006452
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
      bInterfaceSubClass      2 SFF-8020i, MMC-2 (ATAPI)
      bInterfaceProtocol     80
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```

I've experimented with a couple of fixes for related problems that I've found. Most notably, updating the pci and usb id databases, and configuring udev to not run hdparm on USB devices. This did not help.

Here is the output of lspci | grep USB on the two servers that show the problem:

```

00:1d.0 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 (rev 09)
00:1d.1 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 (rev 09)
00:1d.2 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 (rev 09)
00:1d.7 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller (rev 09)

```

```


00:12.0 USB controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.5 USB controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller

```

As you can see, two completely different chipsets. I've tried plugging the devices into multiple ports. Didn't help.

Here is what "udevadm monitor" thinks about me inserting one of the drives:

```

monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[1319211397.682974] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1
SUBSYSTEM=usb
DEVNAME=bus/usb/001/005
DEVTYPE=usb_device
PRODUCT=1234/5678/5
TYPE=0/0/0
BUSNUM=001
DEVNUM=005
SEQNUM=1859
MAJOR=189
MINOR=4

KERNEL[1319211397.683334] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
PRODUCT=1234/5678/5
TYPE=0/0/0
INTERFACE=8/2/80
MODALIAS=usb:v1234p5678d0005dc00dsc00dp00ic08isc02ip50
SEQNUM=1860

KERNEL[1319211397.683499] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10 (scsi)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10
SUBSYSTEM=scsi
DEVTYPE=scsi_host
SEQNUM=1861

KERNEL[1319211397.683512] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10/scsi_host/host10 (scsi_host)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10/scsi_host/host10
SUBSYSTEM=scsi_host
SEQNUM=1862

UDEV  [1319211397.684276] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1
SUBSYSTEM=usb
DEVNAME=/dev/bus/usb/001/005
DEVTYPE=usb_device
PRODUCT=1234/5678/5
TYPE=0/0/0
BUSNUM=001
DEVNUM=005
SEQNUM=1859
ID_VENDOR=VLI_manufacture_String
ID_VENDOR_ENC=VLI\x20manufacture\x20String
ID_VENDOR_ID=1234
ID_MODEL=VLI_Product_String
ID_MODEL_ENC=VLI\x20Product\x20String
ID_MODEL_ID=5678
ID_REVISION=0005
ID_SERIAL=VLI_manufacture_String_VLI_Product_String_0000000000006459
ID_SERIAL_SHORT=0000000000006459
ID_BUS=usb
ID_USB_INTERFACES=:080250:
MAJOR=189
MINOR=4
DEVLINKS=/dev/char/189:4

UDEV  [1319211397.684421] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
PRODUCT=1234/5678/5
TYPE=0/0/0
INTERFACE=8/2/80
MODALIAS=usb:v1234p5678d0005dc00dsc00dp00ic08isc02ip50
SEQNUM=1860

UDEV  [1319211397.684467] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10 (scsi)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10
SUBSYSTEM=scsi
DEVTYPE=scsi_host
SEQNUM=1861

UDEV  [1319211397.684486] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10/scsi_host/host10 (scsi_host)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10/scsi_host/host10
SUBSYSTEM=scsi_host
SEQNUM=1862

KERNEL[1319211398.690581] remove   /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10/scsi_host/host10 (scsi_host)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10/scsi_host/host10
SUBSYSTEM=scsi_host
SEQNUM=1863

KERNEL[1319211398.690595] remove   /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10 (scsi)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10
SUBSYSTEM=scsi
DEVTYPE=scsi_host
SEQNUM=1864

KERNEL[1319211398.690736] remove   /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0 (usb)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
PRODUCT=1234/5678/5
TYPE=0/0/0
INTERFACE=8/2/80
MODALIAS=usb:v1234p5678d0005dc00dsc00dp00ic08isc02ip50
SEQNUM=1865

UDEV  [1319211398.690749] remove   /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10/scsi_host/host10 (scsi_host)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10/scsi_host/host10
SUBSYSTEM=scsi_host
SEQNUM=1863

KERNEL[1319211398.690762] remove   /devices/pci0000:00/0000:00:12.2/usb1/1-1 (usb)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1
SUBSYSTEM=usb
DEVNAME=bus/usb/001/005
DEVTYPE=usb_device
PRODUCT=1234/5678/5
TYPE=0/0/0
BUSNUM=001
DEVNUM=005
SEQNUM=1866
MAJOR=189
MINOR=4

UDEV  [1319211398.690881] remove   /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10 (scsi)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host10
SUBSYSTEM=scsi
DEVTYPE=scsi_host
SEQNUM=1864

UDEV  [1319211398.691161] remove   /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0 (usb)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
PRODUCT=1234/5678/5
TYPE=0/0/0
INTERFACE=8/2/80
MODALIAS=usb:v1234p5678d0005dc00dsc00dp00ic08isc02ip50
SEQNUM=1865

UDEV  [1319211398.691482] remove   /devices/pci0000:00/0000:00:12.2/usb1/1-1 (usb)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1
SUBSYSTEM=usb
DEVNAME=/dev/bus/usb/001/005
DEVTYPE=usb_device
PRODUCT=1234/5678/5
TYPE=0/0/0
BUSNUM=001
DEVNUM=005
SEQNUM=1866
ID_VENDOR=VLI_manufacture_String
ID_VENDOR_ENC=VLI\x20manufacture\x20String
ID_VENDOR_ID=1234
ID_MODEL=VLI_Product_String
ID_MODEL_ENC=VLI\x20Product\x20String
ID_MODEL_ID=5678
ID_REVISION=0005
ID_SERIAL=VLI_manufacture_String_VLI_Product_String_0000000000006459
ID_SERIAL_SHORT=0000000000006459
ID_BUS=usb
ID_USB_INTERFACES=:080250:
MAJOR=189
MINOR=4
DEVLINKS=/dev/char/189:4

KERNEL[1319211399.454557] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1
SUBSYSTEM=usb
DEVNAME=bus/usb/001/006
DEVTYPE=usb_device
PRODUCT=1234/5678/5
TYPE=0/0/0
BUSNUM=001
DEVNUM=006
SEQNUM=1867
MAJOR=189
MINOR=5

KERNEL[1319211399.454878] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
PRODUCT=1234/5678/5
TYPE=0/0/0
INTERFACE=8/2/80
MODALIAS=usb:v1234p5678d0005dc00dsc00dp00ic08isc02ip50
SEQNUM=1868

KERNEL[1319211399.455039] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host11 (scsi)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host11
SUBSYSTEM=scsi
DEVTYPE=scsi_host
SEQNUM=1869

KERNEL[1319211399.455052] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host11/scsi_host/host11 (scsi_host)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host11/scsi_host/host11
SUBSYSTEM=scsi_host
SEQNUM=1870

UDEV  [1319211399.455864] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1
SUBSYSTEM=usb
DEVNAME=/dev/bus/usb/001/006
DEVTYPE=usb_device
PRODUCT=1234/5678/5
TYPE=0/0/0
BUSNUM=001
DEVNUM=006
SEQNUM=1867
ID_VENDOR=VLI_manufacture_String
ID_VENDOR_ENC=VLI\x20manufacture\x20String
ID_VENDOR_ID=1234
ID_MODEL=VLI_Product_String
ID_MODEL_ENC=VLI\x20Product\x20String
ID_MODEL_ID=5678
ID_REVISION=0005
ID_SERIAL=VLI_manufacture_String_VLI_Product_String_0000000000006459
ID_SERIAL_SHORT=0000000000006459
ID_BUS=usb
ID_USB_INTERFACES=:080250:
MAJOR=189
MINOR=5
DEVLINKS=/dev/char/189:5

UDEV  [1319211399.455994] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
PRODUCT=1234/5678/5
TYPE=0/0/0
INTERFACE=8/2/80
MODALIAS=usb:v1234p5678d0005dc00dsc00dp00ic08isc02ip50
SEQNUM=1868

UDEV  [1319211399.456265] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host11 (scsi)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host11
SUBSYSTEM=scsi
DEVTYPE=scsi_host
SEQNUM=1869

UDEV  [1319211399.456389] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host11/scsi_host/host11 (scsi_host)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host11/scsi_host/host11
SUBSYSTEM=scsi_host
SEQNUM=1870

KERNEL[1319211404.448147] add      /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host11/target11:0:0 (scsi)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host11/target11:0:0
SUBSYSTEM=scsi
DEVTYPE=scsi_target
SEQNUM=1871

KERNEL[1319211404.448165] add 

```

Kernel versions on the two servers are:

```

Linux vega 2.6.32-30-server #59-Ubuntu SMP Tue Mar 1 22:46:09 UTC 2011 x86_64 GNU/Linux
Linux zangief 2.6.32-34-server #77-Ubuntu SMP Tue Sep 13 20:54:38 UTC 2011 x86_64 GNU/Linux

```

Here's the output of df -h on one of the boxes, to show it's fine with large drives in general:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             919G  1.5G  918G   1% /
none                  1.9G  244K  1.9G   1% /dev
none                  1.9G     0  1.9G   0% /dev/shm
none                  1.9G   48K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
/dev/sda1             938M   49M  842M   6% /boot
/dev/md0              2.8T  886G  1.9T  32% /backup/hot
/dev/sdb1              19T  2.0T   17T  11% /backup/main

```

I'm out of ideas. Has anyone seen this before?

---

### Post by oldfred on 2011-10-21
Are you using LVM or RAID? I know neither.

> /dev/sda1             938M   49M  842M   6% /boot
/dev/md0              2.8T  886G  1.9T  32% /backup/hot
/dev/sdb1             [COLOR=Red] 19T[/COLOR]  2.0T   17T  11% /backup/main

Someone before had strange results with MBR formating of a new 4K drive where it somehow wrapped around and gave weird results. 

You should be using gpt. I think you still use gpt inside the RAID or LVM, but do not know details.

GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by sdetheridge on 2011-10-21
There is a hardware RAID controller in the server. That 19T array shows up as an SD device, although I am also using software Raid1 for another pair of disks.

I don't see how that's relevant though. I included that example just to show that the server can handle drives larger than 3TB.

I understand that I have to use GPT for a 3TB drive though. There is a size limit for MBR. All that is academic however, as parted *hangs* immediately, when trying to create a GPT parition table, as does anything else that attempts to talk to the disk device. (Badblocks, dd, etc.)

The problem is lower level than the filesystem or partition structure. I cannot use the device at all.

---

### Post by oldfred on 2011-10-21
Was the 3TB drive ever in a RAID set? That can confuse things as meta data stays on drive and formating tools then see that and do not work. One user had a brand new drive have RAID meta data (we think) as removing that solved his issue.

Do **not** run this on any drive you do have RAID on.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by sdetheridge on 2011-10-21
The drive is a brand new drive. (Well, one of the two I hooked up to a Windows box and made a new GPT partition table and partition to see if that worked, but didn't.)

Completely fresh never-used drive with no data on it whatsoever. Any access with parted, fdisk, dd, badblocks, etc, just hangs the machine. Block-level access does not work. (e.g. "badblocks -s /dev/sde" hangs at 0.00%, and needs to be kill -9'd)

750G drive in identical unit works just fine.

---

### Post by diasf on 2011-10-21
first of all, i just skimmed the thread, didn't really read it :)

But I've seen some problems on 3Tb drives, that are formatted using 4k clusters and everything else thinks the clusters are 512bytes (that was the standard size until now, that is, not all applications really support the 4k blocks... and weirdly enough, ppl report that worked uned previous ubuntu versions...)

And no, no idea of a solution...

---

### Post by oldfred on 2011-10-23
Some BIOS settings can influence a drive's visability. But if your RAID works I would think the BIOS has correct settings.

---

### Post by sdetheridge on 2011-10-24
> **diasf said:**
> first of all, i just skimmed the thread, didn't really read it :)

But I've seen some problems on 3Tb drives, that are formatted using 4k clusters and everything else thinks the clusters are 512bytes (that was the standard size until now, that is, not all applications really support the 4k blocks... and weirdly enough, ppl report that worked uned previous ubuntu versions...)

And no, no idea of a solution...

Again, this is a block-level access problem. The drive has not yet been formatted.

And yes, I've checked BIOS settings. Couldn't find anything that would cause things to work differently. (I've played with USB-related settings such as legacy support, to no avail.

I think this is a kernel problem tbh. I might find a more appropriate place to report the issue.

---

### Post by sdetheridge on 2011-10-24
Looking into it further, I think this is really the key part of the problem:
```

[237605.160101] usb 1-1: reset high speed USB device using ehci_hcd and address 8
[237606.317608] sd 13:0:0:0: [sde] Unhandled error code
[237606.317612] sd 13:0:0:0: [sde] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[237606.317614] sd 13:0:0:0: [sde] CDB: Read(16): 88 00 00 00 00 01 5d 50 a3 a0 00 00
[237606.317620] end_request: I/O error, dev sde, sector 5860533152
...

```

Whenever I try and use the device, I see something similar. The sector number is always in the vicinity of ~5860533100. This is larger than a 32-bit number. This happens even when I try to just dd a bunch of zeros to the beginning of the drive.

---

### Post by sdetheridge on 2011-10-25
It's a kernel bug, and has been solved solved by a patch. See here:
[http://marc.info/?t=131946682100002&r=1&w=2](http://marc.info/?t=131946682100002&r=1&w=2)

Hopefully the patch will make it into an official kernel update at some point. In the meantime, I had to recompile the kernel from source and apply the patch manually.

---

