---
title: "Can't find USB storage device"
date: 2010-08-13
forum: Hardware
---

### Post by ender4 on 2010-08-13
I am thoroughly confused.

I have a cheap generic mp3 player that until now I haven't had any trouble with.  Now it won't automatically mount with either GNOME or KDE.  Worse, I can't figure out what device to mount (if it is even there).  I have tried plugging it into different USB ports to no effect.  I have not trouble mounting other USB devices (a flash drive was mounted from /dev/sdb1 ) and I can mount the mp3 player without any trouble on another box which also runs Lucid.

The applicable line from lsusb is:
```
Bus 002 Device 007: ID 0402:5668 ALi Corp.
```
```
fdisk -l
```
only outputs information about /dev/sda, which is my harddrive

the output from dmesg is:
```

[ 1512.128171] usb 2-2: new high speed USB device using ehci_hcd and address 6
[ 1512.263874] usb 2-2: configuration #1 chosen from 1 choice
[ 1512.264696] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1512.265095] usb-storage: device found at 6
[ 1512.265100] usb-storage: waiting for device to settle before scanning
[ 1522.556197] usb 2-2: reset high speed USB device using ehci_hcd and address 6
[ 1635.699445] usb 2-2: USB disconnect, address 6
[ 1645.736204] usb 2-2: new high speed USB device using ehci_hcd and address 7
[ 1645.871660] usb 2-2: configuration #1 chosen from 1 choice
[ 1645.872545] scsi9 : SCSI emulation for USB Mass Storage devices
[ 1645.872953] usb-storage: device found at 7
[ 1645.872958] usb-storage: waiting for device to settle before scanning
[ 1656.164191] usb 2-2: reset high speed USB device using ehci_hcd and address 7

```

Any help would be appreciated.

---

### Post by dino99 on 2010-08-13
check that usbmount and usbutils are installed

sudo update-usbids && sudo update-pciids

mountmanager is an easy tool to deal with partitions and devices, install it and set your prefs into: system admin mountmanager

---

### Post by ender4 on 2010-08-13
usbmount and usbutils are installed, and the device does not show up in mountmanager.

Also, my device isn't lifted in 
"blkid -t TYPE=vfat"

---

### Post by ender4 on 2010-08-13
the output from "lsusb -v" is:
```



Bus 002 Device 004: ID 0402:5668 ALi Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0402 ALi Corp.
  idProduct          0x5668 
  bcdDevice            0.02
  iManufacturer           3 ALi Corp.
  iProduct                1 Audio Player
  iSerial                 2 00101000101410066868
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
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
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              16
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```


Does anyone know what device file I need to mount for it?

---

### Post by ender4 on 2010-08-17
I have gotten it to work a couple of times, but I'm not sure what I did to get it working, and it is sort of off and on.  Any ideas on how to *consistently* mount the drive?

---

### Post by lazyfirecloud on 2011-02-04
Hi,
Just wondering if anyone had found a solution to this. 
It works for me on my desktop running Lucid Lynx but no longer works my laptop running Maverick (it used to before I upgraded). I do get different messages in /var/log/messages

Lucid (auto mounts, no problems):
```
Feb  3 20:23:59 desktop kernel: [2615645.929940] usb 1-5: new high speed USB device using ehci_hcd and address 5
Feb  3 20:23:59 desktop kernel: [2615646.082191] usb 1-5: configuration #1 chosen from 1 choice
Feb  3 20:23:59 desktop kernel: [2615646.083391] scsi6 : SCSI emulation for USB Mass Storage devices
Feb  3 20:24:04 desktop kernel: [2615651.072061] scsi 6:0:0:0: Direct-Access     Qualcomm MMC Storage      2.31 PQ: 0 ANSI: 2
Feb  3 20:24:04 desktop kernel: [2615651.072609] sd 6:0:0:0: Attached scsi generic sg4 type 0
Feb  3 20:24:04 desktop kernel: [2615651.073899] sd 6:0:0:0: [sdd] 31116288 512-byte logical blocks: (15.9 GB/14.8 GiB)
Feb  3 20:24:04 desktop kernel: [2615651.074590] sd 6:0:0:0: [sdd] Write Protect is off
Feb  3 20:24:04 desktop kernel: [2615651.076699]  sdd: sdd1
Feb  3 20:24:04 desktop kernel: [2615651.081188] sd 6:0:0:0: [sdd] Attached SCSI removable disk
Feb  3 20:24:15 desktop kernel: [2615661.821750]  sdd: sdd1
Feb  3 20:25:07 desktop kernel: [2615713.996879] usb 1-5: USB disconnect, address 5
```

Maverick:
```
Feb  3 20:43:06 laptop kernel: [265256.617280] usb 1-1.2: new high speed USB device using ehci_hcd and address 29
Feb  3 20:43:06 laptop kernel: [265256.731711] scsi12 : usb-storage 1-1.2:1.0
Feb  3 20:43:07 laptop usb_modeswitch: switching 04e8:f000 (Qualcomm, Incorporated: Qualcomm CDMA Technologies MSM)
Feb  3 20:43:08 laptop kernel: [265258.089649] usb 1-1.2: USB disconnect, address 25
```

In Maverick, it doesn't get assigned to a /dev/sd* (I did a diff of 'ls /dev' before and after plugging it in)

```

$ lsusb
...
Bus 001 Device 029: ID 04e8:f000 Samsung Electronics Co., Ltd 
...

```

```

$ cat /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/uevent
MAJOR=189
MINOR=28
DEVNAME=bus/usb/001/029
DEVTYPE=usb_device
DRIVER=usb
PRODUCT=4e8/f000/0
TYPE=0/0/0
BUSNUM=001
DEVNUM=029

```

I tried:
```

$ sudo modprobe -r ehci_hcd
FATAL: Module ehci_hcd is builtin
$ sudo mount -t vfat /dev/bus/usb/001/029 mp3/
mount: /dev/bus/usb/001/029 is not a block device
$ sudo mount -t usbfs /dev/bus/usb/001/029 mp3/
mount: unknown filesystem type 'usbfs'

```

I can mount my portable external USB hard drive just fine, but not this device ever since I upgraded to Maverick. It used to work, and still works on Lucid but I can't figure out what's going on.

Anyone?

---

### Post by temporary88 on 2011-09-27
This is known bug:
[https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/755342](https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/755342)

This is a problem with the usb-modeswitch, if you disable it in /etc/usb_modeswitch.conf => DisableSwitching=1 then it works

---

### Post by lazyfirecloud on 2011-09-28
Thanks temporary88.
Unfortunately, I can't test this since I switched to an Android phone since my last post. But I'm sure it will be helpful for anyone who finds themselves on this forum =)

---

