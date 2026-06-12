---
title: "no audio over HDMI on NVIDIA Corporation GF116 High Definition Audio Controller or In"
date: 2015-12-30
forum: Hardware
---

### Post by kubanc on 2015-12-30
Hello.
I am using **Wily,** **Ubuntu 15.10**

I am trying to bring sound through HDMI cable from my PC to Sony STR-DH520 amplifier.
Sound is working fine when I choose "Line Out *Built in Audio*", but if I try to get audio through HDMI cable (for surround sound) nothing works.

When I plug in HDMI cable into **Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)** Ubuntu does not recognize that the cable was plugged in.
When I plug in HDMI cable into **NVIDIA Corporation GF116 High Definition Audio Controller [10de:0bee] (rev a1)** Ubuntu recognizes that the HDMI cable was plugged in, but there is no sound on my speakers. I can see that there is sound playing because in pavucontrol the sound bar is going up and down...

Here is my info
**lspci -nnk | grep -iA2 audio**
```

00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: ASRock Incorporation Device [1849:7892]
    Kernel driver in use: snd_hda_intel
--
01:00.1 Audio device [0403]: NVIDIA Corporation GF116 High Definition Audio Controller [10de:0bee] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:83be]
    Kernel driver in use: snd_hda_intel

```

Info when my HDMi cable is connected to **NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)**: with audo device **NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)**
[B]aplay -l
[/B]```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
[B]aplay -L
[/B]```
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround21:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
hdmi:CARD=PCH,DEV=2
    HDA Intel PCH, HDMI 2
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dmix:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions

```

Here is my info when my HDMi cable is connected to Intel [B]Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04):
aplay -l
[/B]```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
**aplay -L**
```
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround21:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
hdmi:CARD=PCH,DEV=2
    HDA Intel PCH, HDMI 2
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dmix:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions

```

If you need any other information please let me know.
Thank you for your help

---

### Post by kubanc on 2016-01-05
Hello,
I still need help.
Anyone?

---

### Post by SeijiSensei on 2016-01-05
Are you using the proprietary NVIDIA driver?  Try running "sudo apt-get install nvidia-current" and see if that helps.

In pavucontrol, make sure you have selected the correct output in the Output tab.

---

### Post by kubanc on 2016-01-10
> **SeijiSensei said:**
> Are you using the proprietary NVIDIA driver?  Try running "sudo apt-get install nvidia-current" and see if that helps.

In pavucontrol, make sure you have selected the correct output in the Output tab.

and yes, I have set HDMI for audio device in pavucontrol
This is my current video configuration:


  *-display               
       description: VGA compatible controller
       product: GF116 [GeForce GTX 550 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:32 memory:f4000000-f5ffffff memory:e0000000-e7ffffff memory:e8000000-ebffffff ioport:e000(size=128) memory:f6000000-f607ffff
  *-display UNCLAIMED
       description: Display controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)

---

### Post by SeijiSensei on 2016-01-10
That's a description of the hardware but not the driver you're using.  By default Ubuntu uses the "nouveau" open-source driver for NVIDIA cards, not the proprietary driver from NVIDIA itself.  It's not clear from your response which driver you are using.

Can you disable the Intel adapter from the BIOS?  If so, give that a shot.

Have you tried listening on the analog audio jack to see if the sound is being routed through that?

---

### Post by kubanc on 2016-01-13
> **SeijiSensei said:**
> That's a description of the hardware but not the driver you're using.  By default Ubuntu uses the "nouveau" open-source driver for NVIDIA cards, not the proprietary driver from NVIDIA itself.  It's not clear from your response which driver you are using.

Can you disable the Intel adapter from the BIOS?  If so, give that a shot.

Have you tried listening on the analog audio jack to see if the sound is being routed through that?

I am using NVIDIA binary driver - version 352.63 from nvidia-352(proprietary, tested)

I have already disabled intel video card in BISO UEFI, because If I did not do that, there would be no video from my NVIDIA graphic card.
Analog audio jack is working fine.

---

