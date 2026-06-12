---
title: "Nokia E71 USB error"
date: 2008-10-29
forum: General Help
---

### Post by al3omdah on 2008-10-29
Guys I'm facing little problem with Nokia E71 connection in USB cable
I have connected my nokia E71 (CONNECT PC TO WEB MODE)  to my laptop using USB and executed in terminal the command below

**:~$ lsusb -vd 0421:00aa**


I got this result !

Bus 002 Device 002: ID 0421:00aa Nokia Mobile Phones 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0421 Nokia Mobile Phones
  idProduct          0x00aa 
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
    iConfiguration          4 
    bmAttributes         0xc0
      Self Powered
    MaxPower               20mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              6 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

**another result when I executed this command **
:~$ mn-tool

- Device: eth0  ----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        08:00:46:E4:2E:1E

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Settings

so here you are my questions ?
- How can I configure driver properly ?
- How can I connect to the Internet using GPRS with nokia E71 (Configuration step by step)[B]

I'm running Ubuntu 8.10
                - the Intrepid Ibex - released in October 2008[/B]

Finally I have already read details on this thread [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/257045]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/257045")

---

### Post by VanguardOutlander on 2008-11-03
I'm keen to hear any stories of getting the Nokia E71 working in Linux too! :popcorn:

---

### Post by CnlPepper on 2008-11-03
[edit]sorry I didn't read the original post properly.[/edit]

---

### Post by al3omdah on 2008-11-06
So anybody can help to fix this issue !!?

---

### Post by Kevbert on 2008-11-06
Have you tried using Wammu/Gammu ? It's in the repos so you will be able to get it via Synaptic.

---

### Post by ThomasNovin on 2008-11-07
Using the E71 as a modem in Intrepid should be easy, it's supported according to bug #257045 on LP.

Has anyone tried reading/sending SMS etc. witm Wammu?

---

### Post by al3omdah on 2008-11-16
I can easily connect to the internet with USB cable for e71 I have reinstalled Ubunut and so far every thing is ok I have discovered Network Manager can do the rest for successful connection   

Thank you **Kevbert** for **Wammu/Gammu** nice applications 



Thanks again

---

