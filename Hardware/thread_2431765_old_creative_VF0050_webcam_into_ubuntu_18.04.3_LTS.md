---
title: "old creative VF0050 webcam into ubuntu 18.04.3 LTS"
date: 2019-11-21
forum: Hardware
---

### Post by iqtc on 2019-11-21
Dear community,

We are trying to use an old webcam in a new Ubuntu 18.04.3 LTS.  We haven't too much experience with this and we are not sure if it's possible.

The webcam model is: Creative Live! VF0050 

The operating system detects it once it's connected through USB and the webcam led gets illuminated. But programs like Cheese and other similar we've tested, tell us there are no video devices. We guess we are not using a correct driver but we have no idea which would work or where to look at.

This is the dmesg output just immediately after connecting the webcam via USB 2.0:
```

[ 1450.974242] usb 4-3: new full-speed USB device number 4 using ohci-pci
[ 1451.169336] usb 4-3: New USB device found, idVendor=041e, idProduct=4036
[ 1451.169341] usb 4-3: New USB device strings: Mfr=1, Product=2,
SerialNumber=0
[ 1451.169344] usb 4-3: Product: WebCam Live!
[ 1451.169346] usb 4-3: Manufacturer: Creative Labs
[ 1451.171443] gspca_main: gspca_zc3xx-2.14.0 probing 041e:4036
[ 1452.539531] input: gspca_zc3xx as
/devices/pci0000:00/0000:00:12.0/usb4/4-3/input/input22
```

Once connected, the device appears in: /dev/video0

But we get this error when we try:
```

cat /dev/video0
cat: /dev/video0: Invalid argument

```

This is part of the lsusb -v output:
```

Bus 004 Device 004: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x041e Creative Technology, Ltd
  idProduct          0x4036 Webcam Live!/Live! Pro
  bcdDevice            1.00
  iManufacturer           1
  iProduct                2
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          193
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
    (Bus Powered)
    MaxPower              160mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
...

```

We have installed also v4l and v4l2 packets trying to make it work:
v4l-conf
libv4l-0
v4l-utils
qv4l2
motio
ffmpeg

When trying another driver:
vlc v4l2:///dev/video0
We get the following error:
```

VLC media player 3.0.8 Vetinari (revision 3.0.8-0-gf350b6b5a7)
[00005600b343d4b0] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00005600b3518350] skins2 interface error: cannot instantiate dialogs provider
[00005600b3518350] [cli] lua interface: Listening on host "*console".
VLC media player 3.0.8 Vetinari
Command Line Interface initialized. Type `help' for help.
> libv4l2: error setting pixformat: Device or resource busy
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error setting pixformat: Invalid argument
[00007fae5c0010e0] v4l2 demux error: cannot set format: Invalid argument
[00007fae5c0010e0] v4l2 demux error: not a radio tuner device
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error setting pixformat: Device or resource busy
libv4l2: error setting pixformat: Invalid argument
[00007fae5c004260] v4l2 stream error: cannot set format: Invalid argument
[00007fae58000c40] main input error: Your input can't be opened
[00007fae58000c40] main input error: VLC is unable to open the MRL 'v4l2:///dev/video0'. Check the log for details.

```

We've found some old theads in ubuntu forums about this webcam, but most of the links we've tried to follow are now unavailable. 

We are not sure what else to test. Any advice is welcome!

Best regards,
iqtc

---

### Post by howefield on 2019-11-21
Thread moved to the "*Hardware*" forum.

---

