---
title: "Sound for root, but not for an ordinary user. Why?"
date: 2016-03-12
forum: Hardware
---

### Post by Keith_Beef on 2016-03-12
Hardware is a Dell R610. I know, the fans are noisy; but still, I want to be able to make sounds from it.

I recently bought an inexpensive USB sound interface to test things, in order to know whether it would be worthwhile shelling out for a 24-bit, 192kHz interface.

Before plugging in the external USB sound interface
```
keith@jupiter:~$ sudo lsusb -t
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    |__ Port 3: Dev 2, If 0, Class=Hub, Driver=hub/3p, 480M

```
After plugging in the external USB sound interface
```
keith@jupiter:~$ sudo lsusb -t
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    |__ Port 3: Dev 2, If 0, Class=Hub, Driver=hub/3p, 480M
        |__ Port 1: Dev 3, If 0, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 1: Dev 3, If 1, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 1: Dev 3, If 2, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 1: Dev 3, If 3, Class=Human Interface Device, Driver=usbhid, 12M
```

Connected the speaker output to the input of old Lansing amplified speakers,
with the volume turned low.

Installed Rosegarden with all its required dependencies.
Prompted to configure jackd2 to enable realtime access priority,
not checked, should come back and do that later.
Installed jack-tooks and gjacktransport.

Installed alsa-utils, alsa-base, alsa-player with all their required dependencies.


```
keith@jupiter:~/Downloads$ sudo aplay -l
[sudo] password for keith: 
**** List of PLAYBACK Hardware Devices ****
card 0: Device [USB Sound Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
keith@jupiter:~/Downloads$ lsmod | grep snd
snd_usb_audio         176128  0 
snd_usbmidi_lib        36864  1 snd_usb_audio
snd_hwdep              16384  1 snd_usb_audio
snd_rawmidi            32768  1 snd_usbmidi_lib
snd_seq_device         16384  1 snd_rawmidi
snd_pcm               102400  1 snd_usb_audio
snd_timer              32768  1 snd_pcm
snd                    81920  7 snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_rawmidi,snd_usbmidi_lib,snd_seq_device
soundcore              16384  1 snd
```

```
keith@jupiter:~/Downloads$ lspci -v | grep -A7 -i "audio"
```
Nothing returned… not good

```
keith@jupiter:~/Downloads$ sudo ls -al /dev/bus/usb/
total 0
drwxr-xr-x 8 root root 160 Mar 12 07:28 .
drwxr-xr-x 3 root root  60 Mar 12 07:28 ..
drwxr-xr-x 2 root root 100 Mar 12 10:02 001
drwxr-xr-x 2 root root  60 Mar 12 07:28 002
drwxr-xr-x 2 root root  60 Mar 12 07:28 003
drwxr-xr-x 2 root root  60 Mar 12 07:28 004
drwxr-xr-x 2 root root  60 Mar 12 07:28 005
drwxr-xr-x 2 root root  60 Mar 12 07:28 006
```

Remebering this:
```
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    |__ Port 3: Dev 2, If 0, Class=Hub, Driver=hub/3p, 480M
        |__ Port 1: Dev 3, If 0, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 1: Dev 3, If 1, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 1: Dev 3, If 2, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 1: Dev 3, If 3, Class=Human Interface Device, Driver=usbhid, 12M
```

```
keith@jupiter:~/Downloads$ sudo ls -al /dev/bus/usb/001/003
crw-rw-r-- 1 root root 189, 2 Mar 12 10:02 /dev/bus/usb/001/003
```

```
lsusb -s 1:3
Bus 001 Device 003: ID 0d8c:0102 C-Media Electronics, Inc. CM106 Like Sound Device
```


```
keith@jupiter:~/Downloads$ lsusb -s 1:3 -v >> sound_device_from_lsusb.txt
Couldn't open device, some information will be missing
```

Contents of the sound_device_from_lsusb.txt file. (this is long…)

```
Bus 001 Device 003: ID 0d8c:0102 C-Media Electronics, Inc. CM106 Like Sound Device
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0d8c C-Media Electronics, Inc.
  idProduct          0x0102 CM106 Like Sound Device
  bcdDevice            0.10
  iManufacturer           0 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          534
    bNumInterfaces          4
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
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength          200
        bInCollection           2
        baInterfaceNr( 0)       1
        baInterfaceNr( 1)       2
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bNrChannels             8
        wChannelConfig     0x063f
          Left Front (L)
          Right Front (R)
          Center Front (C)
          Low Freqency Enhancement (LFE)
          Left Surround (LS)
          Right Surround (RS)
          Side Left (SL)
          Side Right (SR)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             4
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 8
        bSourceID               4
        bControlSize            1
        bmaControls( 0)      0x01
          Mute Control
        bmaControls( 1)      0x02
          Volume Control
        bmaControls( 2)      0x02
          Volume Control
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 9
        bSourceID               4
        bControlSize            1
        bmaControls( 0)      0x01
          Mute Control
        bmaControls( 1)      0x02
          Volume Control
        bmaControls( 2)      0x02
          Volume Control
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                25
        bDescriptorType        36
        bDescriptorSubtype      4 (MIXER_UNIT)
        bUnitID                12
        bNrInPins               3
        baSourceID( 0)          1
        baSourceID( 1)          9
        baSourceID( 2)         11
        bNrChannels             8
        wChannelConfig     0x063f
          Left Front (L)
          Right Front (R)
          Center Front (C)
          Low Freqency Enhancement (LFE)
          Left Surround (LS)
          Right Surround (RS)
          Side Left (SL)
          Side Right (SR)
        iChannelNames           0 
        bmControls         0x00
        bmControls         0x00
        bmControls         0x00
        iMixer                  0 
        junk at descriptor end: 00 00 00 00 00 00 00 00 00
      AudioControl Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                13
        bSourceID              12
        bControlSize            1
        bmaControls( 0)      0x01
          Mute Control
        bmaControls( 1)      0x02
          Volume Control
        bmaControls( 2)      0x02
          Volume Control
        bmaControls( 3)      0x02
          Volume Control
        bmaControls( 4)      0x02
          Volume Control
        bmaControls( 5)      0x02
          Volume Control
        bmaControls( 6)      0x02
          Volume Control
        bmaControls( 7)      0x02
          Volume Control
        bmaControls( 8)      0x02
          Volume Control
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0301 Speaker
        bAssocTerminal          0
        bSourceID              13
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      4 (MIXER_UNIT)
        bUnitID                17
        bNrInPins               2
        baSourceID( 0)          9
        baSourceID( 1)         11
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        bmControls         0x00
        iMixer                  0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID            10
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               7
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      5 (SELECTOR_UNIT)
        bUnitID                 7
        bNrInPins               4
        baSource( 0)            8
        baSource( 1)           15
        baSource( 2)           16
        baSource( 3)            2
        iSelector               0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             6
        wTerminalType      0x0603 Line Connector
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                15
        bSourceID               6
        bControlSize            1
        bmaControls( 0)      0x01
          Mute Control
        bmaControls( 1)      0x02
          Volume Control
        bmaControls( 2)      0x02
          Volume Control
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                11
        bSourceID               6
        bControlSize            1
        bmaControls( 0)      0x01
          Mute Control
        bmaControls( 1)      0x02
          Volume Control
        bmaControls( 2)      0x02
          Volume Control
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             5
        wTerminalType      0x0605 SPDIF interface
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 2
        bSourceID              17
        bControlSize            1
        bmaControls( 0)      0x01
          Mute Control
        bmaControls( 1)      0x02
          Volume Control
        bmaControls( 2)      0x02
          Volume Control
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                16
        bSourceID               5
        bControlSize            1
        bmaControls( 0)      0x01
          Mute Control
        bmaControls( 1)      0x00
        bmaControls( 2)      0x00
        iFeature                0 
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
        bLength                14
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             8
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            2 Discrete
        tSamFreq[ 0]        44100
        tSamFreq[ 1]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0310  1x 784 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
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
        bLength                14
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            2 Discrete
        tSamFreq[ 0]        44100
        tSamFreq[ 1]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x00c4  1x 196 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
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
        bLength                14
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             4
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            2 Discrete
        tSamFreq[ 0]        44100
        tSamFreq[ 1]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0188  1x 392 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
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
        bLength                14
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             6
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            2 Discrete
        tSamFreq[ 0]        44100
        tSamFreq[ 1]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0248  1x 584 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
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
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0188  1x 392 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
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
        bTerminalLink          10
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                14
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            2 Discrete
        tSamFreq[ 0]        44100
        tSamFreq[ 1]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x00c8  1x 200 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      50
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0003  1x 3 bytes
        bInterval               1
```

```
keith@jupiter:~/Downloads$ sudo alsamixer
```
This displayed the levels for the USB device, I lowered the levels from 100% down
to 81%.

```
keith@jupiter:~/Downloads$ sudo aplay audiocheck.net_hdchirp_88k_-3dBFS_log.wav
Playing WAVE 'audiocheck.net_hdchirp_88k_-3dBFS_log.wav' : Signed 16 bit Little Endian, Rate 88200 Hz, Mono
```

I hear a short burst of sound.

```
keith@jupiter:~/Downloads$ sudo aplay Media-Convert_test2_PCM_Mono_VBR_8SS_48000Hz.wav 
Playing WAVE 'Media-Convert_test2_PCM_Mono_VBR_8SS_48000Hz.wav' : Unsigned 8 bit, Rate 44100 Hz, Mono
```

I hear what sounds like a clip from a cartoon.

```
keith@jupiter:~/Downloads$ sudo aplay Media-Convert_test2_PCM_Mono_VBR_8SS_48000Hz.wav 
Playing WAVE 'Media-Convert_test2_PCM_Mono_VBR_8SS_48000Hz.wav' : Unsigned 8 bit, Rate 44100 Hz, Mono
keith@jupiter:~/Downloads$ aplay Media-Convert_test2_PCM_Mono_VBR_8SS_48000Hz.wav 
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4248:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4248:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4248:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4727:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:722: audio open error: No such file or directory
```

No sound, either.

OK, so sound is working from ALSA, so long as I am root.

How can I make sound available for all users?

---

### Post by Keith_Beef on 2016-03-28
Well, I don't even have sound as root, now.

I decided to change the positions of a few things in the rack and route the cables differently so that they were neater and so it would be easier for me to switch on or off individual peripherals to reduce power consumption and noise.

So now the USB sound card is plugged in at the back of the computer, rather than the front. 
```
$ sudo lsusb -t
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=Audio, Driver=snd-usb-audio, 12M
    |__ Port 1: Dev 2, If 1, Class=Audio, Driver=snd-usb-audio, 12M
    |__ Port 1: Dev 2, If 2, Class=Audio, Driver=snd-usb-audio, 12M
    |__ Port 1: Dev 2, If 3, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    |__ Port 3: Dev 3, If 0, Class=Hub, Driver=hub/3p, 480M
```

This seems to have messed up ALSA.
```
$ sudo speaker-test 

speaker-test 1.0.27.2

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4248:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4248:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4248:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4727:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -2,No such file or directory
```

The USB device is now identified as "card 1"
```
$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Device [USB Sound Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

It had been "card 1" (copied from the previous post)
```
keith@jupiter:~/Downloads$ sudo aplay -l
[sudo] password for keith: 
**** List of PLAYBACK Hardware Devices ****
card 0: Device [USB Sound Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Well, I plugged the USB device into the front port again, reloaded the ALSA drivers, but it has not changed anything.
```
$ sudo lsusb -t
[sudo] password for keith: 
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    |__ Port 3: Dev 3, If 0, Class=Hub, Driver=hub/3p, 480M
        |__ Port 2: Dev 4, If 0, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 2: Dev 4, If 1, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 2: Dev 4, If 2, Class=Audio, Driver=snd-usb-audio, 12M
        |__ Port 2: Dev 4, If 3, Class=Human Interface Device, Driver=usbhid, 12M
```

```
$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Device [USB Sound Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #
```0

```
$ sudo /sbin/alsa force-reload
Unloading ALSA sound driver modules: snd-usb-audio snd-usbmidi-lib snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
Loading ALSA sound driver modules: snd-usb-audio snd-usbmidi-lib snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
```

```
~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Device [USB Sound Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I've been trying to find out how to force this USB device to be card 0…I would have expected this to be the case, since this computer does not have a built-in sound device.
The instructions I found [here]("http://alsa.opensrc.org/MultipleCards") are hard to apply to my case, since my config file is very different.

```
$ cat /etc/modprobe.d/alsa-base.conf 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```

---

