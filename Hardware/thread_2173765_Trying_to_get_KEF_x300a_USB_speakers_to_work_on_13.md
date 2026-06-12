---
title: "Trying to get KEF x300a USB speakers to work on 13.04"
date: 2013-09-11
forum: Hardware
---

### Post by bimbo on 2013-09-11
I recently bought a pair of KEF X300a USB speakers which sound tremendous under Windows. I have so far failed to get them to work on Linux (despite some Googling, my problem does not seem to mirror the other people's reports):

Plugging in the speaker on USB, I get a whole bunch of the following in dmesg
```
[45405.178248] 12:1:1: usb_set_interface failed (-71)
[45405.178657] 12:1:1: usb_set_interface failed (-71)
[45405.179093] 12:1:1: usb_set_interface failed (-71)
[45405.180206] 12:1:1: usb_set_interface failed (-71)
[45405.180467] 12:1:1: usb_set_interface failed (-71)
[45405.180800] 12:1:1: usb_set_interface failed (-71)
[45405.181191] xhci_hcd 0000:00:14.0: URB transfer length is wrong, xHC issue? req. len = 0, act. len = 4294967288
[45405.181318] 12:1:1: cannot set freq 44100 to ep 0x1
[45405.181794] 12:1:1: cannot set freq 44100 to ep 0x1
[45405.183281] 12:1:1: usb_set_interface failed (-71)
[45405.183569] 12:1:1: usb_set_interface failed (-71)
[45405.183955] 12:1:1: usb_set_interface failed (-71)
[45405.184466] 12:1:1: usb_set_interface failed (-71)
[45405.185011] 12:1:1: usb_set_interface failed (-71)

```

And the usb stack seems to be a bit confused by what it sees (namely it does not seem to know the devices name) but does figure out that it is USB DAC:
```
buz@buztp:~$ sudo lsusb -v -s :012

Bus 003 Device 012: ID 27ac:1000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x27ac 
  idProduct          0x1000 
  bcdDevice            3.70
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          128
    bNumInterfaces          2
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
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              2 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           40
        bInCollection           1
        baInterfaceNr( 0)       1
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               6 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                10
        bSourceID               1
        bControlSize            1
        bmaControls( 0)      0x00
        bmaControls( 1)      0x03
          Mute Control
          Volume Control
        bmaControls( 2)      0x03
          Mute Control
          Volume Control
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             6
        wTerminalType      0x0301 Speaker
        bAssocTerminal          0
        bSourceID              10
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
      iInterface              4 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              4 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                20
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           3
        bBitResolution         24
        bSamFreqType            4 Discrete
        tSamFreq[ 0]        44100
        tSamFreq[ 1]        48000
        tSamFreq[ 2]        88200
        tSamFreq[ 3]        96000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0246  1x 582 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress         129
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              0 Decoded PCM samples
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0003  1x 3 bytes
        bInterval               1
        bRefresh                4
        bSynchAddress           0
Device Status:     0x8d60
  (Bus Powered)
  Debug Mode

```



Interestingly, aplay also lists the USB DAC and even gets the device's name correct:
```
buz@buztp:~$  sudo aplay -lv
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Speaker [KEF X300A Speaker], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Edit: Now alsamixer sees the USB devices and crashes as expected. So next step is to simply patch alsa, I guess...

---

### Post by bimbo on 2013-09-11
I am trying to do the change suggestd here: [http://thread.gmane.org/gmane.linux.alsa.user/37231](http://thread.gmane.org/gmane.linux.alsa.user/37231)

But fixing the Alsa build process seems to be over my current capabilities (and I've been using Linux on and off for 13 years now....). Does anyone have a script (or fixed tarball) of an alsa driver package that works without dpkg-buildpackage and other associated Debian tools? The alsa-driver package from the project website sadly does not compile on Ubuntu and I can't compile the Ubuntu sources manually, either (apparently Debian decided to get rid of some non-free drivers but didn't properly patch that)...

---

### Post by xenopeek on 2013-09-22
I've been considering these speakers but I've been put off by the very little information that can be found about these and Linux compatibility. I contacted somebody from technical support for KEF and the feedback I got was that the KEF's DAC needs to have a USB asynchronous connection (and it needs to be in control of that). From what I understand, that's not working. Couple of things you could try:

1-See if your motherboard has a USB2.0 connection, or even a USB1.0 connection. It might work when you connect to an older USB interface perhaps. At least for some other DACs I've been reading up, that was what made them work on Linux.

2-You're running Ubuntu 13.04, so with an ancient kernel no longer supported by the kernel developers. Worth a shot to download the Ubuntu 13.10 beta and boot from the Live session and see if it works with that--with the newer kernel (which might have a fix for this). Doesn't really matter which edition you try; it's the kernel you want to test. Links to current beta's here: [http://www.omgubuntu.co.uk/2013/09/ubuntu-13-10-beta-1-released-available-for-download](http://www.omgubuntu.co.uk/2013/09/ubuntu-13-10-beta-1-released-available-for-download)

Edit: technical support person from KEF was friendly and helpful, but it was pretty clear they don't officially or unofficially support Linux :( Hope you get these to work!

---

### Post by solars on 2014-01-21
any news on this?

I've received mine today, did a quick test, they are recognized as a device in alsamixer but I cannot select it due to some error
didn't find the error msg yet, will try again tomorrow

---

### Post by chuil on 2014-07-18
Any joy with the kef speakers? I have been holding back this purchase for same reason (linux support).

---

### Post by solars on 2014-07-21
> **chuil said:**
> Any joy with the kef speakers? I have been holding back this purchase for same reason (linux support).

I didn't have time to try again yet, I have them connected to a windows machine which I need for photoshop.
However, the speakers are definitely worth it, probably the best desktop speakers of this size. I also have other KEF speakers and
I have to admit I'm amazed by the quality.

---

### Post by Bucky Ball on 2014-07-21
13.04 is no longer supported. Suggest you upgrade to a supported release, 12.04 LTS or 14.04 LTS. We no longer give support for EOL (end-of-life) releases here. 

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by solars on 2014-07-21
> **Bucky Ball said:**
> 13.04 is no longer supported. Suggest you upgrade to a supported release, 12.04 LTS or 14.04 LTS. We no longer give support for EOL (end-of-life) releases here. 

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

Please not that the topic is older :)

---

### Post by Elfy on 2014-07-21
closed

---

