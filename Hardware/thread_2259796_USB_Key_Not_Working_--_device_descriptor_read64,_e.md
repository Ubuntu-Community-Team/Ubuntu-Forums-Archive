---
title: "USB Key Not Working -- device descriptor read/64, error -110"
date: 2015-01-07
forum: Hardware
---

### Post by Jean-Pascal_Peltie on 2015-01-07
Hello,

I have a [Kingston DT 100 G2]("http://www.kingston.com/en/support/technical/products?model=dt100g2") which is not being detected on  any system (Windows, MacOSX, Linux). On Linux, I have the following **dmesg**:

```

[ 1086.804150] usb 4-3: new high-speed USB device number 17 using ehci-pci
[ 1086.941593] usb 4-3: New USB device found, idVendor=0951, idProduct=1653
[ 1086.941604] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1086.941611] usb 4-3: Product: DT 100 G2
[ 1086.941617] usb 4-3: Manufacturer: Kingston
[ 1086.941623] usb 4-3: SerialNumber: 0013729B6F4BBB30656200FD
[ 1086.942204] usb-storage 4-3:1.0: USB Mass Storage device detected
[ 1086.943090] scsi7 : usb-storage 4-3:1.0
[ 1108.948134] usb 4-3: reset high-speed USB device number 17 using ehci-pci
[ 1124.060131] usb 4-3: device descriptor read/64, error -110
[ 1139.276127] usb 4-3: device descriptor read/64, error -110
[ 1139.492122] usb 4-3: reset high-speed USB device number 17 using ehci-pci

```

I  checked around and saw the messages about USB power, but: i) as said  above, the problem exists on several, different laptops; ii) I already  tried unplugging power cord and battery; iii) I have no other, external  USB device; and iv) **lsusb -v** shows a (reasonable) 200mA MaxPower:

```

Bus 004 Device 025: ID 0951:1653 Kingston Technology Data Traveler 100 G2 8 GiB
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0951 Kingston Technology
  idProduct          0x1653 Data Traveler 100 G2 8 GiB
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
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
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
Device Status:     0x0000
  (Bus Powered)

```

Bottom  line question is: should I throw away my USB stick, or is there a way  to fix and reformat it? (I don't mind losing existing data)

Thanks,

**JPP**.

---

### Post by plucky on 2015-01-07
> Bottom line question is: should I throw away my USB stick, or is there a way to fix and reformat it? (I don't mind losing existing data)

Try gparted to re-format the drive,but I would run "Check Device" first in one of the gparted menus.

You might have to install gparted.

From a terminal ```
sudo apt-get install gparted
```

Good Luck

---

### Post by Jean-Pascal_Peltie on 2015-01-07
> **plucky said:**
> Try gparted to re-format the drive,but I would run "Check Device" first in one of the gparted menus.

Thanks. The device doesn't appear in GParted (only /dev/sda hard drive), even after a GParted -> Update Devices run ...

---

### Post by sudodus on 2015-01-07
If you un-plug and re-plug in several computers and the pendrive does not appear as a device in gparted or for example the output of the following commands

```
sudo parted -l
sudo fdisk -lu
sudo lsblk -fm
```

there is not much we can do. It is dead.

---

### Post by Jean-Pascal_Peltie on 2015-01-07
> **sudodus said:**
> ```
sudo parted -l
sudo fdisk -lu
sudo lsblk -fm
```

None of them shows the USB device. I guess this unfortunately answers my question ...

Thanks for the quick reply!

**JPP**.

---

