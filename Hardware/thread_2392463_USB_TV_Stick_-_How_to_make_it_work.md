---
title: "USB TV Stick - How to make it work"
date: 2018-05-21
forum: Hardware
---

### Post by pete-br on 2018-05-21
I own this USB Stick: [https://www.linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV382_(id_0x1f71:0x3301)](https://www.linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV382_(id_0x1f71:0x3301))

How do I make it work?


lsusb -v -s 002:004
```
Bus 002 Device 004: ID 1f71:3301  
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1f71 
  idProduct          0x3301 
  bcdDevice            1.00
  iManufacturer           3 
  iProduct                4 
  iSerial                 2 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           83
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
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
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
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               4
```

part of dmesg output:
```
[    3.855534] usb 2-1.3: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256
[    3.858525] usb 2-1.3: New USB device found, idVendor=1f71, idProduct=3301
[    3.858527] usb 2-1.3: New USB device strings: Mfr=3, Product=4, SerialNumber=2
[    3.858529] usb 2-1.3: Product: USB TV Box
[    3.858530] usb 2-1.3: Manufacturer: Gadmei
[    3.858532] usb 2-1.3: SerialNumber: 330000000009
```

uname -mrs
```
Linux 4.15.0-20-generic x86_64
```

I have Ubuntu 18.04.

---

### Post by TheFu on 2018-05-21
What have you tried?

---

### Post by pete-br on 2018-05-21
Since the device is recognized at least, shown from the dmesg output, I simply tried using it.

I tried using VLC to open the device as 'TV - analog' with /dev/video0 and setting a frequency I know to be a valid channel.
VLC shows a black screen and no further errors.

I tried tvtime -d /dev/video0 but it doesn't work. It shows errors on the commandline something about posting a bug report to linuxtv.

Something has to be wrong, but I can't figure it out.


If I unplug the device, then do dmesg and check VLC, there is no /dev/video0.
Then I plug it back in and do dmesg again, the added part in dmesg is:
```
[ 8116.666341] usb 2-1.3: new high-speed USB device number 6 using ehci-pci
[ 8116.778038] usb 2-1.3: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256
[ 8116.781288] usb 2-1.3: New USB device found, idVendor=1f71, idProduct=3301
[ 8116.781294] usb 2-1.3: New USB device strings: Mfr=3, Product=4, SerialNumber=2
[ 8116.781298] usb 2-1.3: Product: USB TV Box
[ 8116.781302] usb 2-1.3: Manufacturer: Gadmei
[ 8116.781305] usb 2-1.3: SerialNumber: 330000000009
[ 8116.783056] usbtv 2-1.3:1.0: Fushicai USBTV007 Audio-Video Grabber
```


I am not sure, but maybe the wrong driver is being loaded.
This is a TV tuner for analog TV. It has worked as one in Windows.
Someone here: [https://ubuntuforums.org/archive/index.php/t-1501570.html](https://ubuntuforums.org/archive/index.php/t-1501570.html) is suggesting the same thing.

---

### Post by yancek on 2018-05-21
When you run the command below, does the output show /dev/video0?  If not, what does it  show?

```
ls /dev/video*
```

---

### Post by pete-br on 2018-05-22
```
ls /dev/video*
/dev/video0
```

and /dev/video0 is shown in yellow.

---

### Post by pete-br on 2018-05-24
I just wanted to let people know I have been editing the information regarding this device on linuxtv.org:
[https://www.linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV382_(id_0x1f71:0x3301)](https://www.linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV382_(id_0x1f71:0x3301))

I have added notes that the device as things are right now may not fully function.

It contains a chip that I cannot with certainty identify. If someone knows more about this, their input would be appreciated. Pictures are on the linuxtv page.

---

### Post by leunam12 on 2018-05-25
These are the commands that I use with my card.

To watch on VLC
```
vlc 'v4l2c://'
```
To watch on mplayer
```
mplayer /dev/video0
```
List inputs.
```
v4l2-ctl -d /dev/video0 --list-inputs
```
Set the Input. (number changes according to the results from the previous command).
```
v4l2-ctl -d /dev/video0 -i 1
```
Set the channel
```
ivtv-tune -c 3
```

---

### Post by pete-br on 2018-05-28
```

$ vlc 'v4l2c://'
VLC media player 3.0.2 Vetinari (revision 3.0.2-0-gd7b653cf14)

Then when trying to open menu 'Media' -> Recent -> 'v4l2c:///dev/video0'
In the terminal windows appears the error:
[00007f530014be00] deinterlace filter error: unknown or incompatible deinterlace mode "x" for packed format

```

```

$ v4l2-ctl -d /dev/video0 --list-inputs
ioctl: VIDIOC_ENUMINPUT
    Input       : 0
    Name        : Composite
    Type        : 0x00000002 (Camera)
    Audioset    : 0x00000000
    Tuner       : 0x00000000
    Standard    : 0x000000000000F9FF (PAL-B/B1/G/H/I/D/D1/K/M/60 NTSC-M/M-JP/443/M-KR)
    Status      : 0x00000000 (ok)
    Capabilities: 0x00000004 (SDTV standards)

    Input       : 1
    Name        : S-Video
    Type        : 0x00000002 (Camera)
    Audioset    : 0x00000000
    Tuner       : 0x00000000
    Standard    : 0x000000000000F9FF (PAL-B/B1/G/H/I/D/D1/K/M/60 NTSC-M/M-JP/443/M-KR)
    Status      : 0x00000000 (ok)
    Capabilities: 0x00000004 (SDTV standards)

```

```

$ ivtv-tune -c 3
ioctl VIDIOC_S_FREQUENCY failed

```

---

### Post by pete-br on 2018-05-28
```

$ mplayer /dev/video0
Creating config file: /home/username/.mplayer/config
MPlayer 1.3.0 (Debian), built with gcc-7 (C) 2000-2016 MPlayer Team
do_connect: could not connect to socket
connect: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
libavformat version 57.83.100 (external)
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed

```

No image, no sound, no nothing. Whatever I try.

---

### Post by pete-br on 2018-05-28
Someone here is showing his output from v4l2-ctl -d /dev/video0 --list-inputs
[https://forum.ubuntuusers.de/topic/ich-will-hauppauge-wintv-pvr-usb2-unter-hardy/](https://forum.ubuntuusers.de/topic/ich-will-hauppauge-wintv-pvr-usb2-unter-hardy/)

It shows:
Input   : 0
Name    : television

Mine does not have an input named television.
I still think I need a different driver or some driver adjustment.
If the chip at linuxtv could be identified, that could be a starting point:
[https://www.linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV382_(id_0x1f71:0x3301)](https://www.linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV382_(id_0x1f71:0x3301))
It's the BCK0XM or 2136-30-BCKOOR-1625 chip.

---

