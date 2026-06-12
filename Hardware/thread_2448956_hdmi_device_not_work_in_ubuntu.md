---
title: "hdmi device not work in ubuntu"
date: 2020-08-17
forum: Hardware
---

### Post by fredy50 on 2020-08-17
Hello,

I installed ubuntu on the new laptop i get (ASUS TUF Gaming A17 FX706IU-H7145T).
But then i install windows 10 my HDMI works. but then it comes to ubuntu i can't get it to work.

i run this code: (lspci):
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1630
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 1631
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1632
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1633
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1632
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1634
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1634
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1634
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1632
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1635
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1635
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 51)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1448
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1449
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 144a
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 144b
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 144c
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 144d
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 144e
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 144f
01:00.0 VGA compatible controller: NVIDIA Corporation Device 2191 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 1aeb (rev a1)
01:00.2 USB controller: NVIDIA Corporation Device 1aec (rev a1)
01:00.3 Serial bus controller [0c80]: NVIDIA Corporation Device 1aed (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device c822
04:00.0 Non-Volatile memory controller: Kingston Technology Company, Inc. Device 500c (rev 01)
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 1636 (rev f0)
05:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1637
05:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 15df
05:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 1639
05:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Device 1639
05:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Device 15e2 (rev 01)
05:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Device 15e3
06:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 81)
06:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 81)
```

also run another command: aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic_1 [HD-Audio Generic], device 0: ALC256 Analog [ALC256 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```


Can someone help me with that?
Thanks for your time !

---

### Post by fredy50 on 2020-08-17
aplay -L
```
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions
sysdefault:CARD=Generic_1
    HD-Audio Generic, ALC256 Analog
    Default Audio Device
front:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC256 Analog
    Front speakers
surround21:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC256 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC256 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC256 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC256 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC256 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC256 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC256 Analog
    Direct sample mixing device
dsnoop:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC256 Analog
    Direct sample snooping device
hw:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC256 Analog
    Direct hardware device without any conversions
plughw:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC256 Analog
    Hardware device with all software conversions
```

---

