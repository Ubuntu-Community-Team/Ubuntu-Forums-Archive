---
title: "2004 ibm thinkpad usb help"
date: 2010-03-08
forum: Hardware
---

### Post by bman11 on 2010-03-08
hi my friend gave me an old think pad i believ eit is a 2004 standard school laptop and i decided to put ubuntu on it because windows is dildos ;) but anyways. i have it all set up and i have multiple linux computers. i am not exactly the best but can manage. i am having a problem with the laptops usb. they worked before i put ubuntu on here. i have looked for drivers but am not exactly sure what i am looking for. 
thank you for the help

---

### Post by tgalati4 on 2010-03-08
Several thinkpads of that era have defective USB controller chips.  USB works out of the box.  There are no drivers to install.

Open a terminal and post the output of:

lsusb

---

### Post by bman11 on 2010-03-08
i have done what you said and i get a reply of

-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by tgalati4 on 2010-03-08
Try:

lsusb -vv

It should look like:  (on a thinkpad T43p)

tgalati4@tpad-Gloria7 ~ $ lsusb -vv

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
    MaxPower                0mA
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
    MaxPower                0mA
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
    MaxPower                0mA
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
    MaxPower                0mA
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
    MaxPower                0mA
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


And that is with nothing plugged in.

Plug in a flash drive or camera or ipod then run it again.

---

### Post by bman11 on 2010-03-09
-laptop:~$ lsusb -vv

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
    MaxPower                0mA
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
    MaxPower                0mA
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
    MaxPower                0mA
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
    MaxPower                0mA
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


that is what i get. with the drive plugged in. so is there any way to make this work?

---

### Post by tgalati4 on 2010-03-09
If you have plugged in a USB, external hard drive, and it doesn't show up, then perhaps you need to provide external power.  Does your drive have a power port to plug in?

It's also possible that your USB 5VDC power has burned out.  Also a common problem with thinkpads.

Do you have a USB flash drive to plug in and see if you can read that?

---

### Post by bman11 on 2010-03-09
i have tried both a usb thumndrive and and externally powered harddrive and nothing responds.

before putting this ubuntu on this laptop it had never had a problem with the usb.
i believe the problem lies is in the drivers

---

### Post by tgalati4 on 2010-03-09
Plug in the thumbdrive; open a terminal, post the output of:

dmesg | tail -50

---

### Post by bman11 on 2010-03-11
-laptop:~$ dmesg | tail -50
[   79.662460]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   79.662464]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   79.662468]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   79.662471]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   79.662475]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   79.662479]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   79.662481] cfg80211: We intersect both of these and get:
[   79.662483] cfg80211: Regulatory domain: 98
[   79.662486]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   79.662489]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   79.662497] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[   79.662500] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[   79.662503] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   79.662506] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[   79.662509] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[   79.662513] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[   79.662516] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[   79.662520] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[   79.662523] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[   79.662526] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[   79.662530] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[   79.662533] cfg80211: Leaving channel 5500 MHz intact on phy0 - no rule found in band on Country IE
[   79.662537] cfg80211: Leaving channel 5520 MHz intact on phy0 - no rule found in band on Country IE
[   79.662540] cfg80211: Leaving channel 5540 MHz intact on phy0 - no rule found in band on Country IE
[   79.662544] cfg80211: Leaving channel 5560 MHz intact on phy0 - no rule found in band on Country IE
[   79.662547] cfg80211: Leaving channel 5580 MHz intact on phy0 - no rule found in band on Country IE
[   79.662551] cfg80211: Leaving channel 5600 MHz intact on phy0 - no rule found in band on Country IE
[   79.662554] cfg80211: Leaving channel 5620 MHz intact on phy0 - no rule found in band on Country IE
[   79.662557] cfg80211: Leaving channel 5640 MHz intact on phy0 - no rule found in band on Country IE
[   79.662561] cfg80211: Leaving channel 5660 MHz intact on phy0 - no rule found in band on Country IE
[   79.662564] cfg80211: Leaving channel 5680 MHz intact on phy0 - no rule found in band on Country IE
[   79.662568] cfg80211: Leaving channel 5700 MHz intact on phy0 - no rule found in band on Country IE
[   79.662571] cfg80211: Leaving channel 5745 MHz intact on phy0 - no rule found in band on Country IE
[   79.662575] cfg80211: Leaving channel 5765 MHz intact on phy0 - no rule found in band on Country IE
[   79.662578] cfg80211: Leaving channel 5785 MHz intact on phy0 - no rule found in band on Country IE
[   79.662582] cfg80211: Leaving channel 5805 MHz intact on phy0 - no rule found in band on Country IE
[   79.662585] cfg80211: Leaving channel 5825 MHz intact on phy0 - no rule found in band on Country IE
[   79.662595] cfg80211: Current regulatory domain updated by AP to: US
[   79.662597]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   79.662601]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   90.092231] wlan0: no IPv6 routers present
[  650.984405] hub 1-0:1.0: unable to enumerate USB device on port 4
[  651.172529] hub 1-0:1.0: unable to enumerate USB device on port 4
[  651.360537] hub 1-0:1.0: unable to enumerate USB device on port 4
[  651.548527] hub 1-0:1.0: unable to enumerate USB device on port 4
[  651.736524] hub 1-0:1.0: unable to enumerate USB device on port 4
[  651.924412] hub 1-0:1.0: unable to enumerate USB device on port 4
[  652.112400] hub 1-0:1.0: unable to enumerate USB device on port 4
[  652.300523] hub 1-0:1.0: unable to enumerate USB device on port 4
[  652.488521] hub 1-0:1.0: unable to enumerate USB device on port 4



thats what i get. is this good or bad?

---

### Post by tgalati4 on 2010-03-11
I think the port is defective.  The response should be the vendor:product ID numbers and what the device is.  Is this machine dual-boot with Windows?  If so, do the ports work in Windows?  Try them all.

---

### Post by bman11 on 2010-03-11
it does not dual boot with windows. is there a set of drivers i could run though for ibm thinkpads?

---

### Post by tgalati4 on 2010-03-11
There are no drivers to speak of.  The USB hardware detection is built into the kernel and HAL (hardware abstraction layer).  HAL will report if a device is hooked up with the Vendor ID and the Product ID and Unknown device driver if it can't find a suitable software driver for it.  Since any device that you plug into your USB port does not register with:

dmesg | tail

Then one has to assume that the port is defective in some fashion.  USB has really never been a problem in linux.  Certainly some obscure devices don't work correctly in linux, but they still show up in dmesg.  

How many USB ports does your machine have?

What devices (be specific with make and model) have you tested in those ports?

Do those devices work on another machine?

Do you have a desktop machine available to run an Ubuntu Live CD so you can test your devices on the desktop machine?  If you are running the same version of Ubuntu on both the laptop and the desktop and the desktop USB ports work and the laptop doesn't, then that points to a hardware problem.

---

