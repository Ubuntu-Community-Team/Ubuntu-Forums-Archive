---
title: "Turn in the Ubuntu PC by IR remote"
date: 2017-01-09
forum: Hardware
---

### Post by uxie on 2017-01-09
Hi there!

Just bought the simplest IR remote control
[IMG]https://s27.postimg.org/hzegk2x6n/ir_remote.jpg[/IMG]
for the only purpose - I want to turn my PC on directly from the sofa :D I can do it by my wireless keyboard or mouse but small RC would be better. BIOS settings should be ok (waking up by USB keyboard/mouse turned on). Thought that IR remote just emulates keyboard and mouse - but it doesn't work... After full system load (Ubuntu 16.10) remote works normally.

Tried to solve the issue by reading similar topics on askubuntu and other sources but no success there :(

**lsusb** command shows the following:
> [INDENT]Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 09da:054f A4Tech Co., Ltd. 
**Bus 003 Device 002: ID 1d57:ad02 Xenta SE340D PC Remote Control**
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/INDENT]



**lsusb -vvv** seems also ok:
> Bus 003 Device 002: ID 1d57:ad02 Xenta SE340D PC Remote Control
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1d57 Xenta
  idProduct          0xad02 SE340D PC Remote Control
  bcdDevice            1.05
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
     [B] (Bus Powered)
      Remote Wakeup[/B]
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      **bInterfaceProtocol      1 Keyboard**
    
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      **bInterfaceProtocol      2 Mouse**     

Tried **cat /proc/acpi/wakeup** and see only one USB1 with "disabled" status:
> Device   S-state     Status   Sysfs node
CIR     S3   *disabled
PS2K     S4   *disabled
PS2M     S4   *disabled
**USB1     S3   *disabled**
RP01     S4   *disabled  pci:0000:00:1c.0
RP02     S4   *disabled
RP03     S4   *disabled  pci:0000:00:1c.2
RP04     S4   *disabled
RP05     S4   *disabled
RP06     S4   *disabled
RP07     S4   *disabled
RP08     S4   *disabled
GLAN     S4   *disabled
EHC1     S4   *enabled   pci:0000:00:1d.0
EHC2     S4   *enabled   pci:0000:00:1a.0
XHC     S4   *enabled   pci:0000:00:14.0
HDEF     S4   *disabled  pci:0000:00:1b.0
PEG0     S4   *disabled
PEGP     S4   *disabled
PEG1     S4   *disabled
PEG2     S4   *disabled

Appreciate any help! Thanks!

---

### Post by TheFu on 2017-01-10
Think this is completely dependent on the hardware.

[http://kodi.wiki/view/HOW-TO:Suspend_and_wake_in_Ubuntu](http://kodi.wiki/view/HOW-TO:Suspend_and_wake_in_Ubuntu) might help.

---

