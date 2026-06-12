---
title: "7-port powered USB hub not recognized after upgraded to 14.04"
date: 2016-07-16
forum: Hardware
---

### Post by petyabest on 2016-07-16
Hello,

I have a self-powered 7-port USB hub, which is worked correctly under Ubuntu 12.04.
Due to Ubuntu 16.04 release, I decided to upgrade my release from 12.04 to 14.04 (I using older releases than the top all the time.)

After the upgrade process completed, my 7-port USB hub is not recognized correctly anymore.

It seems like the hub is recognized as a 4-port USB hub instead of 7-port hub.
Thus the devices connected to the hub does not recognizes at the system start up.

After that I plugged in a new USB device into a **low-numbered port**, and the device with any previously connected hardware gets to be recognized correctly.
If I connect the device into a higher numbered port, it does not working.

Here is the dmesg output when the system started up:
```

[  668.031447] usb 2-1.2: new high-speed USB device number 25 using ehci-pci
[  668.124492] usb 2-1.2: New USB device found, idVendor=214b, idProduct=7000
[  668.124503] usb 2-1.2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[  668.124509] usb 2-1.2: Product: USB2.0 HUB
[  668.125609] hub 2-1.2:1.0: USB hub found
[  668.125757] hub 2-1.2:1.0: 4 ports detected

```

As I can see only 4 ports detected. (Why???)

This is the lsusb output:
```

Bus 002 Device 025: ID 214b:7000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x214b 
  idProduct          0x7000 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 USB2.0 HUB
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x00e0
    Ganged power switching
    Ganged overcurrent protection
    TT think time 32 FS bits
    Port indicators
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0303 lowspeed power enable connect
   Port 3: 0000.0503 highspeed power enable connect
   Port 4: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```

After a new device connected to a lower numbered port any other devices also gets recognized:
```

[ 1322.504951] usb 2-1.2.3: new high-speed USB device number 33 using ehci-pci
[ 1322.600366] usb 2-1.2.3: New USB device found, idVendor=0930, idProduct=6545
[ 1322.600379] usb 2-1.2.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1322.600385] usb 2-1.2.3: Product: DataTraveler 2.0
[ 1322.600390] usb 2-1.2.3: Manufacturer: Kingston
[ 1322.600395] usb 2-1.2.3: SerialNumber: 001D0F1314D55B89080E0569
[ 1322.600944] usb-storage 2-1.2.3:1.0: USB Mass Storage device detected
[ 1322.602598] scsi8 : usb-storage 2-1.2.3:1.0
[ 1322.805316] usb 2-1.2.4.2: new low-speed USB device number 34 using ehci-pci
[ 1322.901370] usb 2-1.2.4.2: New USB device found, idVendor=046d, idProduct=c05a
[ 1322.901382] usb 2-1.2.4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1322.901388] usb 2-1.2.4.2: Product: USB Optical Mouse
[ 1322.901393] usb 2-1.2.4.2: Manufacturer: Logitech
[ 1322.904797] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.4/2-1.2.4.2/2-1.2.4.2:1.0/input/input20
[ 1322.905068] hid-generic 0003:046D:C05A.0008: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1.2.4.2/input0
[ 1323.105614] usb 2-1.2.4.3: new high-speed USB device number 35 using ehci-pci
[ 1323.199839] usb 2-1.2.4.3: New USB device found, idVendor=14cd, idProduct=8168
[ 1323.199851] usb 2-1.2.4.3: New USB device strings: Mfr=1, Product=3, SerialNumber=2
[ 1323.199857] usb 2-1.2.4.3: Product: USB Mass Storage Device
[ 1323.199862] usb 2-1.2.4.3: Manufacturer: USB Reader  
[ 1323.199867] usb 2-1.2.4.3: SerialNumber: 816820090724
[ 1323.200527] usb-storage 2-1.2.4.3:1.0: USB Mass Storage device detected
[ 1323.201242] scsi9 : usb-storage 2-1.2.4.3:1.0
[ 1323.602806] scsi 8:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 1323.604588] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 1324.200012] scsi 9:0:0:0: Direct-Access     USB Mass  Storage Device       PQ: 0 ANSI: 0 CCS
[ 1324.200506] sd 9:0:0:0: Attached scsi generic sg3 type 0
[ 1324.203279] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[ 1324.734295] sd 8:0:0:0: [sdb] 3966976 512-byte logical blocks: (2.03 GB/1.89 GiB)
[ 1324.735215] sd 8:0:0:0: [sdb] Write Protect is off
[ 1324.735223] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1324.736138] sd 8:0:0:0: [sdb] No Caching mode page found
[ 1324.736149] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1324.740216] sd 8:0:0:0: [sdb] No Caching mode page found
[ 1324.740228] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1324.786038]  sdb: sdb1
[ 1324.790543] sd 8:0:0:0: [sdb] No Caching mode page found
[ 1324.790556] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1324.790565] sd 8:0:0:0: [sdb] Attached SCSI removable disk

```

And the lsusb output after the low-numbered port also connected:
```

Bus 002 Device 032: ID 214b:7000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x214b 
  idProduct          0x7000 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 USB2.0 HUB
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x00e0
    Ganged power switching
    Ganged overcurrent protection
    TT think time 32 FS bits
    Port indicators
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0303 lowspeed power enable connect
   Port 3: 0000.0503 highspeed power enable connect
   Port 4: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```

How can I use this hub correctly again?

Thanks for your help!

---

### Post by petyabest on 2016-07-17
Hello,

Finally I found the solution...
The problem was the Ubuntu's USB Power Management failed on my USB hub.
This hub is a self-powered hub, so it does not require ANY power current from the internal USB port.

The solution is: We have to disable the USB Power Management.

In the */etc/defaults/grub* file I changed the following line:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"

```

(I've added a new parameter: *usbcore.autosuspent=-1*)

After that I ran `*sudo update-grub*`, then reboot.
After that my 7-port USB hub worked properly again.

I found this solution at: [http://askubuntu.com/a/534464](http://askubuntu.com/a/534464)

---

