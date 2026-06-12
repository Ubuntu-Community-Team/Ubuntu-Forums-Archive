---
title: "Windows Mobile 6 device not being recognized"
date: 2008-07-22
forum: Hardware
---

### Post by fwaokda on 2008-07-22
I've followed these instructions to a 'T'.  
[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

I have gotten all the way to the step where you need to run 'synce-pls'.
Once I've ran that I get this message in terminal.

```
fwaokda@fwaokda-laptop:~$ synce-pls
** Message: Hal reports no devices connected

** (process:11894): WARNING **: No devices connected to odccm
synce-pls: Could not find configuration at path '(Default)'

```

If anyone can help it would be greatly appreciated... THANKS!

---

### Post by fwaokda on 2008-07-22
I type in lsusb and it's listed in the list there... so whats the deal?

---

### Post by plinydogg on 2008-07-23
Same problem here.

---

### Post by ^[H3ad-Tr1p]^ on 2008-08-18
have you had solved this problem?

I've the same

thank you

---

### Post by climberjc on 2009-01-04
> **'^[H3ad-Tr1p]^ said:**
> have you had solved this problem?

I've the same

thank you

Same here. Also another guy from a different post thread:
igknighted;6456578
[http://ubuntuforums.org/showthread.php?t=1024814&highlight=Hal+reports+no+devices+connected]("http://ubuntuforums.org/showthread.php?t=1024814&highlight=Hal+reports+no+devices+connected")

---

### Post by climberjc on 2009-01-04
By the way, the device that I am trying to use is a Motorola Q9C. I saw that someone else having this problem was using the same device.

I know that the system sees it, since it shows up in lsusb. Here is the verbose result from ```
lsusb -v
``` for the device:

Bus 004 Device 021: ID 22b8:7008 Motorola PCS 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         1 ?
  bDeviceProtocol         1 Microsoft ActiveSync
  bMaxPacketSize0        64
  idVendor           0x22b8 Motorola PCS
  idProduct          0x7008 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           62
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       239 Miscellaneous Device
      bInterfaceSubClass      1 ?
      bInterfaceProtocol      1 Microsoft ActiveSync
      iInterface              0 
      ** UNRECOGNIZED:  05 24 01 00 01
      ** UNRECOGNIZED:  04 24 02 00
      ** UNRECOGNIZED:  05 24 06 00 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


and when I plug and unplug the device a few times, I get these system messages:

```
xterm -e 'tail -f /var/log/message
```s'

DISCONNECTED DEVICE

Jan 4 15:03:25 jc-workstation kernel: [145504.457389] usb 4-2: USB disconnect, address 19

CONNETED DEVICE

Jan 4 15:03:37 jc-workstation kernel: [145517.208519] usb 4-2: new high speed USB device using ehci_hcd and address 20
Jan 4 15:03.37 jc-workstation kernel: [144517.353148] usb 4-2: configuration # 1 chosen from 1 choice
Jan 4 15:03:37 jc-workstation kernel: [145517.355015] usb 4-2: bad CDC descriptors
Jan 4 15:03:37 jc-workstation kernel: [145517.355395] usb 4-2: bad CDC descriptors

DISCONNETED DEVICE

Jan 4 15:03:46 jc-workstation kernel: [145525.830992] usb 4-2: USB disconnect, address 20

and similar messages for more connections and disconnections. Leaving it plugged in for a while does not result in any additional messages

---

### Post by igknighted on 2009-01-05
Success!

On your phone, go to Start->Settings->Connections->USB, and disable advanced network functionality.  Then plug in the phone again and try synce-pls.  I got a listing of files on the phone as would be expected.  I realize that the synce wiki says that this "advanced functionality" should be enabled, but was encouraged to turn it off on their IRC channel, and alas, success.

---

### Post by climberjc on 2009-01-05
I was under the impression that the 'advanced network functionality' was required for the actual syncing. Without it, it acts as an attached usb stick. For whatever reason, the framework for syncing with evolution or thunderbird was a network communication thing rather than directly modifying the files. 

Is this right, or is 'advanced network functionality' just for things like sharing the internet connection of the phone or something?

---

