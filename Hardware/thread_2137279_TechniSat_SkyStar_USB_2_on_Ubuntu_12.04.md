---
title: "TechniSat SkyStar USB 2 on Ubuntu 12.04"
date: 2013-04-20
forum: Hardware
---

### Post by radopenev on 2013-04-20
Hi all,

I have a TechniSat DVB-PC TV Star 2(SkyStar USB 2) tuner and want to get it running on my Ubuntu 12.04 machine.
lsusb output:
```
test@test-K7NF2-RAID:~$ lsusb
Bus 001 Device 002: ID 13d0:2282 Techsan Electronics Co., Ltd. TechniSat DVB-PC TV Star 2
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
test@test-K7NF2-RAID:~$ lsusb -v -d 13d0:2282

Bus 001 Device 004: ID 13d0:2282 Techsan Electronics Co., Ltd. TechniSat DVB-PC TV Star 2
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x13d0 Techsan Electronics Co., Ltd.
  idProduct          0x2282 TechniSat DVB-PC TV Star 2
  bcdDevice            1.01
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           81
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              222mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           9
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
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
        bEndpointAddress     0x82  EP 2 IN
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x8d  EP 13 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0d  EP 13 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x8e  EP 14 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0e  EP 14 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x8f  EP 15 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               1
test@test-K7NF2-RAID:~$ 
```
 
No any success to make it work!:(
 Kernel module "dvb-usb-technisat-usb2" was added to /etc/modules, but only what I get is:

```
test@test-K7NF2-RAID:~$ dmesg|grep dvb
.....
[    9.134877] usbcore: registered new interface driver dvb_usb_technisat_usb2
.....
test@test-K7NF2-RAID:~$ 
```

The firmware is on the right place 
/lib/firmware/dvb-usb-SkyStar_USB_HD_FW_v17_63.HEX.fw

linux-firmware-nonfree, linux-firmware was instaled
Finally, I have to upgrade to: 
```

test@test-K7NF2-RAID:~$ uname -r
3.8.1-030801-generic
test@test-K7NF2-RAID:~$ lsmod
Module                  Size  Used by
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211395  10 bnep,rfcomm
snd_intel8x0           33458  2 
snd_ac97_codec        110254  1 snd_intel8x0
radeon                892404  2 
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                85934  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
ttm                    72088  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         47749  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
drm                   229318  4 radeon,ttm,drm_kms_helper
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13316  1 radeon
ppdev                  12849  0 
snd                    57014  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_intel8x0,snd_pcm
psmouse                77519  0 
binfmt_misc            17292  1 
shpchp                 32265  0 
ns558                  12654  0 
serio_raw              13031  0 
gameport               15088  2 ns558
i2c_nforce2            12913  0 
parport_pc             32114  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
b2c2_flexcop_usb       13214  0 
b2c2_flexcop           30146  1 b2c2_flexcop_usb
cx24123                18791  1 b2c2_flexcop
cx24113                17702  1 b2c2_flexcop
s5h1420                18259  1 b2c2_flexcop
stv0299                18276  0 
dvb_usb_az6027         22409  0 
stb6100                13547  1 dvb_usb_az6027
stb0899                40869  1 dvb_usb_az6027
dvb_usb_technisat_usb2    13704  0 
stv090x                54028  1 dvb_usb_technisat_usb2
dvb_usb                23898  2 dvb_usb_az6027,dvb_usb_technisat_usb2
dvb_core               90981  5 b2c2_flexcop,stv0299,dvb_usb_az6027,dvb_usb_technisat_usb2,dvb_usb
rc_core                21294  2 dvb_usb_technisat_usb2,dvb_usb
8139too                27407  0 
8139cp                 26728  0 
forcedeth              62275  0 
floppy                 60183  0 
test@test-K7NF2-RAID:~$ 


```

and...............no success again
:confused::confused::confused:

```

test@test-K7NF2-RAID:~$ dmesg|grep usb
[    0.104537] ACPI: bus type usb registered
[    0.104576] usbcore: registered new interface driver usbfs
[    0.104592] usbcore: registered new interface driver hub
[    0.104637] usbcore: registered new device driver usb
[    1.068073] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.068078] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.068082] usb usb1: Product: EHCI Host Controller
[    1.068085] usb usb1: Manufacturer: Linux 3.8.1-030801-generic ehci_hcd
[    1.068088] usb usb1: SerialNumber: 0000:00:02.2
[    1.126043] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.126047] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.126051] usb usb2: Product: OHCI Host Controller
[    1.126054] usb usb2: Manufacturer: Linux 3.8.1-030801-generic ohci_hcd
[    1.126057] usb usb2: SerialNumber: 0000:00:02.0
[    1.182031] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.182035] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.182039] usb usb3: Product: OHCI Host Controller
[    1.182042] usb usb3: Manufacturer: Linux 3.8.1-030801-generic ohci_hcd
[    1.182045] usb usb3: SerialNumber: 0000:00:02.1
[    1.380034] usb 1-6: new high-speed USB device number 2 using ehci-pci
[    1.512365] usb 1-6: New USB device found, idVendor=13d0, idProduct=2282
[    1.512370] usb 1-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    9.134877] usbcore: registered new interface driver dvb_usb_technisat_usb2
[    9.310179] usbcore: registered new interface driver dvb_usb_az6027
[    9.764806] usbcore: registered new interface driver b2c2_flexcop_usb
[ 3895.475714] usb 1-6: USB disconnect, device number 2
[ 3896.092047] usb 1-6: new high-speed USB device number 3 using ehci-pci
[ 3896.224432] usb 1-6: New USB device found, idVendor=13d0, idProduct=2282
[ 3896.224441] usb 1-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 3913.519505] usb 1-6: USB disconnect, device number 3
[ 4396.404036] usb 1-6: new high-speed USB device number 4 using ehci-pci
[ 4396.536426] usb 1-6: New USB device found, idVendor=13d0, idProduct=2282
[ 4396.536435] usb 1-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
test@test-K7NF2-RAID:~$ 


```

It would be really great if someone could give us some hints on that!
Best regards,
radopenev

---

