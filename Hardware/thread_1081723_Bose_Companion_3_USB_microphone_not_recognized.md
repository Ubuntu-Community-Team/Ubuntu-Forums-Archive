---
title: "Bose Companion 3 USB microphone not recognized"
date: 2009-02-26
forum: Hardware
---

### Post by cfmunster on 2009-02-26
I have the Bose Companion 3 USB sound system. Apart from some of the common issues with pulse that have been reported, the speakers work just fine. The microphone, however, does not work at all.

The volume control on the Bose system has a microphone jack and headphone jack for convenience. The headphone jack channels sound to the headphones, but the mic jack does nothing. 

I am running Ubuntu 8.10 with all the latest updates, using Pulse Audio. Here are some troubelshooting details I have picked up from various threads. If I type:

```
# arecord -l
**** List of CAPTURE Hardware Devices ****
#
```

According to this, my computer does not understand that the Bose system has an input device on it, right? Let's check sound devices:

```

#cat /proc/asound/cards
 0 [Audio          ]: USB-Audio - Bose USB Audio
                      Bose Corporation Bose USB Audio at usb-0000:00:02.0-3, full speed
#
```

And this:

```
#aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audio [Bose USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
#
```

Here are the details of the Bose USB device:

```
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=03 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=05a7 ProdID=1020 Rev= 1.00
S:  Manufacturer=Bose Corporation
S:  Product=Bose USB Audio
C:* #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:* If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=01(O) Atr=09(Isoc) MxPS= 576 Ivl=1ms
I:* If#= 2 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=83(I) Atr=03(Int.) MxPS=  64 Ivl=1ms
E:  Ad=03(O) Atr=03(Int.) MxPS=  64 Ivl=1ms
```

And lastly, the full details of the Bose device, extracted from lsusb -v


```
Bus 001 Device 004: ID 05a7:1020 Bose Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05a7 Bose Corp.
  idProduct          0x1020 
  bcdDevice            1.00
  iManufacturer           1 Bose Corporation
  iProduct                2 Bose USB Audio
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          146
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           44
        bInCollection           1
        baInterfaceNr( 0)       1
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bNrChannels             6
        wChannelConfig     0x003f
          Left Front (L)
          Right Front (R)
          Center Front (C)
          Low Freqency Enhancement (LFE)
          Left Surround (LS)
          Right Surround (RS)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                14
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 3
        bSourceID               1
        bControlSize            1
        bmaControls( 0)      0x03
          Mute
          Volume
        bmaControls( 1)      0x00
        bmaControls( 2)      0x00
        bmaControls( 3)      0x00
        bmaControls( 4)      0x00
        bmaControls( 5)      0x00
        bmaControls( 6)      0x00
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             4
        wTerminalType      0x0301 Speaker
        bAssocTerminal          0
        bSourceID               3
        iTerminal               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
```


I am competent but hardly a guru when it comes to linux hardware device setup. If anyone has any ideas as to how I can get the mic to work, or knows that it is impossible, please let me know.


UPDATE: I have re-enabled my motherboard sound system to use the mic for now, so this is not pressing, but it would be useful to know how it works, thanks.

---

