---
title: "USB Audio Device not showing stereo input"
date: 2014-02-21
forum: Hardware
---

### Post by puff2 on 2014-02-21
Hello,

I'm new to this but have been struggling with this issue for awhile.  This is on ubuntu 13.10.  I have this plug-in usb ausdio device shown below.

Take lsusb out (this is the device in question):

Bus 002 Device 004: ID 0c76:1606 JMTek, LLC.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0c76 JMTek, LLC.
  idProduct          0x1606
  bcdDevice            1.00
  iManufacturer           0
  iProduct                1 USB Audio Device
  iSerial                 0
  bNumConfigurations
      1
It is Stereo Out:

 AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID            17
        wTerminalType      0x0301 Speaker
        bAssocTerminal          0
        bSourceID              49
        iTerminal               0
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID            18
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          2
        bSourceID              33
        iTerminal               0

But also, only mono microphone -- advertised as stereo in/stereo out.

AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             1
        wChannelConfig     0x0001
          Left Front (L)
        iChannelNames           0
        iTerminal               0

Does anyone know how to change that bNrChannels from 1 to 2?  I think that is a param associated with stereo.  Anyways, any help would be appreciated, or if anyone knows more about a JMTek device or a driver for it.

Thanks,

---

### Post by TheFu on 2014-02-21
Please post the output from 
```
arecord -l
```

Forget it - probably won't help.

[http://linux-audio.4202.n7.nabble.com/USB-cassette-player-only-recognized-as-mono-device-td84632.html](http://linux-audio.4202.n7.nabble.com/USB-cassette-player-only-recognized-as-mono-device-td84632.html) is related, but doesn't provide a solution.  Could it be that the linux drivers simply don't support stereo? Do you know which driver is being used?

---

### Post by puff2 on 2014-02-21
Thanks for the reply -- I'm not sure how to check the usb driver for this (just calls it a USB Audio Device).  I tried installing alsa-firmware I got from another post that got a tascam to work via usb (thinking it might refresh some of downlevel fw), but did no good -- in fact it caused audacity to freak out a bit, so I needed to install 13.10 again.  So, just seems so simple to modify the channels to 2 instead of 1 for microphone.  The JMTek device was advertised as bidirectional stereo (and I really need the input to be stereo instead of other way around (the device just cost $5.99 plus a little shipping, so no big loss, but if its advertised as stereo input, then it should be lol).  I will check the link you posted, that might shed some light as well.  Thanks.

---

