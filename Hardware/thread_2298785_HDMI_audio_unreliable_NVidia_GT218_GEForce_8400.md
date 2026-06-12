---
title: "HDMI audio unreliable: NVidia GT218 GEForce 8400"
date: 2015-10-13
forum: Hardware
---

### Post by Denis_Papathanasio on 2015-10-13
After using a combination of oem-audio-hda-daily-lts-vivid-dkms and the X.org Nouveau driver to (finally) get sound working (details + background thread here: [http://ubuntuforums.org/showthread.php?t=2295076&p=13360415#post13360415](http://ubuntuforums.org/showthread.php?t=2295076&p=13360415#post13360415) ), those "successful" settings do not survive reboots.

In other words, despite using the same exact driver combination as was working just days earlier, sound no longer works after a simple shutdown/startup or reboot cycle.

I have noticed that alsamixer reports muted S/PDIF devices (which I always unmute), but I'm at a loss for what to do, other than reboot and hope it works.

Is there anything else I should be looking for?

---

### Post by Denis_Papathanasio on 2015-10-14
Here's the output of the alsa-info.sh ( [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo) ) script:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Thu Oct 15 00:25:38 UTC 2015


!!Linux Distribution
!!------------------

Ubuntu 14.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.3 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:       
Product Version:    
Firmware Version:  1.18


!!Kernel Information
!!------------------

Kernel release:    3.13.0-65-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.13.0-65-generic
Library version:    1.0.27.2
Utilities version:  1.0.27.2


!!Loaded ALSA modules
!!-------------------

snd_atiixp
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with ALC655 at 0xfe02a000, irq 17
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcffc000 irq 18


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.5 Multimedia audio controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Audio Controller (rev 02)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:14.5 0401: 1002:4370 (rev 02)
    Subsystem: 103c:3009
--
01:00.1 0403: 10de:0be3 (rev a1)
    Subsystem: 3842:1302


!!Modprobe options (Sound related)
!!--------------------------------

snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------

!!Module: snd_atiixp
    ac97_clock : 48000
    ac97_codec : -1
    ac97_quirk : (null)
    enable : N
    id : (null)
    index : -1
    spdif_aclink : Y

!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : -1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Nvidia ID b
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de000b
Subsystem Id: 0x10de0101
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="ID b Digital", type="HDMI", device=3
  Converter: stream=5, channel=0
  Digital: Enabled Preemphasis Non-Audio Pro
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="HDMI Jack", index=0, device=0
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x04
Codec: Nvidia ID b
Address: 1
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de000b
Subsystem Id: 0x10de0101
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Codec: Nvidia ID b
Address: 2
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de000b
Subsystem Id: 0x10de0101
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Codec: Nvidia ID b
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de000b
Subsystem Id: 0x10de0101
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
--endcollapse--


!!AC97 Codec information
!!----------------------
--startcollapse--

0-0/0: Realtek ALC655 rev 0

PCI Subsys Vendor: 0x103c
PCI Subsys Device: 0x3009

Flags: 0
Revision         : 0x00
Compat. Class    : 0x00
Subsys. Vendor ID: 0xffff
Subsys. ID       : 0xffff

Capabilities     :
DAC resolution   : 16-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=2 LDAC SDAC CDAC DSA=0 SPDIF
Extended status  : SPCV LDAC SDAC CDAC SPDIF=10/11 SPDIF
SPDIF Control    : Consumer PCM Copyright Category=0x2 Generation=1 Rate=48kHz

0:00 = 0000
0:02 = 0101
0:04 = 0000
0:06 = 0000
0:08 = 0000
0:0a = 801e
0:0c = 801f
0:0e = 801f
0:10 = 9717
0:12 = 9f1f
0:14 = 0000
0:16 = 9f1f
0:18 = 0808
0:1a = 0000
0:1c = 0404
0:1e = 0000
0:20 = 0400
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 09c4
0:2a = 05f4
0:2c = bb80
0:2e = bb80
0:30 = bb80
0:32 = bb80
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2820
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0808
0:66 = 0808
0:68 = 0aea
0:6a = 8000
0:6c = 0000
0:6e = 0025
0:70 = 81e0
0:72 = 22e8
0:74 = 8000
0:76 = 0000
0:78 = 0007
0:7a = a092
0:7c = 414c
0:7e = 4760
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  5 Oct 14 19:34 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 11 Oct 14 19:34 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 10 Oct 14 19:34 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  9 Oct 14 19:34 /dev/snd/hwC1D1
crw-rw----+ 1 root audio 116,  8 Oct 14 19:34 /dev/snd/hwC1D2
crw-rw----+ 1 root audio 116,  7 Oct 14 19:34 /dev/snd/hwC1D3
crw-rw----+ 1 root audio 116,  4 Oct 14 19:34 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  3 Oct 14 19:34 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  2 Oct 14 19:34 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  6 Oct 14 20:15 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116,  1 Oct 14 19:34 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Oct 14 19:34 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Oct 14 19:34 .
drwxr-xr-x 3 root root 300 Oct 14 19:34 ..
lrwxrwxrwx 1 root root  12 Oct 14 19:34 pci-0000:00:14.5 -> ../controlC0
lrwxrwxrwx 1 root root  12 Oct 14 19:34 pci-0000:01:00.1 -> ../controlC1


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: ID b Digital [ID b Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [IXP]

Card hw:0 'IXP'/'ATI IXP rev 2 with ALC655 at 0xfe02a000, irq 17'
  Mixer name    : 'Realtek ALC655 rev 0'
  Components    : 'AC97a:414c4760'
  Controls      : 42
  Simple ctrls  : 26
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 30 [97%] [-1.50dB] [on]
  Front Right: Playback 30 [97%] [-1.50dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 8 [26%] [-22.50dB] [off] Capture [off]
  Front Right: Playback 8 [26%] [-22.50dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'PCM' 'Analog In' 'IEC958 In'
  Item0: 'PCM'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 4 [27%] [6.00dB] [on]
  Front Right: Capture 4 [27%] [6.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [NVidia]

Card hw:1 'NVidia'/'HDA NVidia at 0xfcffc000 irq 18'
  Mixer name    : 'Nvidia ID b'
  Components    : 'HDA:10de000b,10de0101,00100200'
  Controls      : 6
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.IXP {
    control.1 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'Master Playback Volume'
        value.0 30
        value.1 30
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 -150
            dbvalue.1 -150
        }
    }
    control.3 {
        iface MIXER
        name 'Center Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'Center Playback Volume'
        value 31
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 0
        }
    }
    control.5 {
        iface MIXER
        name 'LFE Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.6 {
        iface MIXER
        name 'LFE Playback Volume'
        value 31
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 0
        }
    }
    control.7 {
        iface MIXER
        name 'Surround Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.8 {
        iface MIXER
        name 'Surround Playback Volume'
        value.0 31
        value.1 31
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.9 {
        iface MIXER
        name 'Master Mono Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.10 {
        iface MIXER
        name 'Master Mono Playback Volume'
        value 31
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 0
        }
    }
    control.11 {
        iface MIXER
        name 'Beep Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.12 {
        iface MIXER
        name 'Beep Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 15'
            dbmin -4500
            dbmax 0
            dbvalue.0 -4500
        }
    }
    control.13 {
        iface MIXER
        name 'Phone Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.14 {
        iface MIXER
        name 'Phone Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
        }
    }
    control.15 {
        iface MIXER
        name 'Mic Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.16 {
        iface MIXER
        name 'Mic Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
        }
    }
    control.17 {
        iface MIXER
        name 'Mic Boost (+20dB)'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.18 {
        iface MIXER
        name 'Line Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.19 {
        iface MIXER
        name 'Line Playback Volume'
        value.0 8
        value.1 8
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -2250
            dbvalue.1 -2250
        }
    }
    control.20 {
        iface MIXER
        name 'CD Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.21 {
        iface MIXER
        name 'CD Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.22 {
        iface MIXER
        name 'Aux Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.23 {
        iface MIXER
        name 'Aux Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.24 {
        iface MIXER
        name 'PCM Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.25 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 23
        value.1 23
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.26 {
        iface MIXER
        name 'Capture Source'
        value.0 Mic
        value.1 Mic
        comment {
            access 'read write'
            type ENUMERATED
            count 2
            item.0 Mic
            item.1 CD
            item.2 Video
            item.3 Aux
            item.4 Line
            item.5 Mix
            item.6 'Mix Mono'
            item.7 Phone
        }
    }
    control.27 {
        iface MIXER
        name 'Capture Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.28 {
        iface MIXER
        name 'Capture Volume'
        value.0 4
        value.1 4
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 15'
            dbmin 0
            dbmax 2250
            dbvalue.0 600
            dbvalue.1 600
        }
    }
    control.29 {
        iface MIXER
        name 'Mono Output Select'
        value Mix
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mix
            item.1 Mic
        }
    }
    control.30 {
        iface MIXER
        name 'Mic Select'
        value Mic1
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mic1
            item.1 Mic2
        }
    }
    control.31 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.32 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.33 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.34 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.35 {
        iface MIXER
        name 'IEC958 Playback AC97-SPSA'
        value 3
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 3'
        }
    }
    control.36 {
        iface MIXER
        name 'Duplicate Front'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.37 {
        iface MIXER
        name 'Surround Jack Mode'
        value Shared
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Shared
            item.1 Independent
        }
    }
    control.38 {
        iface MIXER
        name 'Channel Mode'
        value '2ch'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 '2ch'
            item.1 '4ch'
            item.2 '6ch'
        }
    }
    control.39 {
        iface MIXER
        name 'IEC958 Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.40 {
        iface MIXER
        name 'IEC958 Playback Source'
        value PCM
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 PCM
            item.1 'Analog In'
            item.2 'IEC958 In'
        }
    }
    control.41 {
        iface MIXER
        name 'External Amplifier'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.42 {
        iface PCM
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        comment {
            access read
            type INTEGER
            count 6
            range '0 - 36'
        }
    }
}
state.NVidia {
    control.1 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.5 {
        iface CARD
        name 'HDMI Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.6 {
        iface PCM
        device 3
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_hda_codec_generic
hid_generic
nvidia
ppdev
snd_hda_intel
ir_lirc_codec
ir_rc5_sz_decoder
usbhid
lirc_dev
ir_mce_kbd_decoder
ir_sanyo_decoder
ir_sony_decoder
ir_jvc_decoder
snd_hda_codec
ir_rc6_decoder
ir_rc5_decoder
snd_hda_core
ir_nec_decoder
rc_streamzap
streamzap
snd_hwdep
hid
rc_core
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
snd_atiixp
snd_ac97_codec
ac97_bus
snd_pcm
snd_seq
serio_raw
edac_core
snd_page_alloc
k8temp
edac_mce_amd
snd_seq_device
snd_timer
i2c_piix4
nfsd
auth_rpcgss
nfs_acl
nfs
lockd
sunrpc
fscache
snd
parport_pc
drm
soundcore
mac_hid
shpchp
lp
parport
pata_acpi
psmouse
tg3
pata_atiixp
ptp
pps_core
floppy
sata_sil


!!Sysfs Files
!!-----------

/sys/class/sound/hwC1D0/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D0/hints:

/sys/class/sound/hwC1D1/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D1/driver_pin_configs:

/sys/class/sound/hwC1D1/user_pin_configs:

/sys/class/sound/hwC1D1/init_verbs:

/sys/class/sound/hwC1D1/hints:

/sys/class/sound/hwC1D2/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D2/driver_pin_configs:

/sys/class/sound/hwC1D2/user_pin_configs:

/sys/class/sound/hwC1D2/init_verbs:

/sys/class/sound/hwC1D2/hints:

/sys/class/sound/hwC1D3/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D3/driver_pin_configs:

/sys/class/sound/hwC1D3/user_pin_configs:

/sys/class/sound/hwC1D3/init_verbs:

/sys/class/sound/hwC1D3/hints:


!!ALSA/HDA dmesg
!!--------------

[   13.628428] IR NEC protocol handler initialized
[   13.634198] snd_hda_core: module verification failed: signature and/or  required key missing - tainting kernel
[   13.641832] IR RC5(x) protocol handler initialized
--
[   13.734259] usbhid: USB HID core driver
[   13.844212] snd_hda_intel 0000:01:00.1: Probing card using HDA DKMS, version 0.201509251532~ubuntu14.04.1
[   13.844358] snd_hda_intel 0000:01:00.1: Disabling MSI
[   13.844366] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   14.849773] init: avahi-cups-reload main process (503) terminated with status 1
--
[   16.229429] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[   16.868048] snd_hda_intel 0000:01:00.1: azx_get_response timeout, switching to polling mode: last cmd=0x200f0000
[   17.393810] snd_hda_codec_hdmi: Unknown symbol snd_hdac_i915_register_notifier (err 0)
[   17.470635] snd_hda_codec_hdmi: Unknown symbol snd_hdac_i915_register_notifier (err 0)
[   17.487126] type=1400 audit(1444865669.930:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=831 comm="apparmor_parser"
--
[   17.496624] type=1400 audit(1444865669.942:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=831 comm="apparmor_parser"
[   17.548063] snd_hda_codec_generic hdaudioC1D0: autoconfig for ID b: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
[   17.548071] snd_hda_codec_generic hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.548075] snd_hda_codec_generic hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.548078] snd_hda_codec_generic hdaudioC1D0:    mono: mono_out=0x0
[   17.548081] snd_hda_codec_generic hdaudioC1D0:    dig-out=0x5/0x0
[   17.548084] snd_hda_codec_generic hdaudioC1D0:    inputs:
[   17.626071] snd_hda_codec_hdmi: Unknown symbol snd_hdac_i915_register_notifier (err 0)
[   17.627469] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.628993] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.658831] snd_hda_codec_hdmi: Unknown symbol snd_hdac_i915_register_notifier (err 0)
[   17.680062] snd_hda_codec_generic hdaudioC1D1: autoconfig for ID b: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
[   17.680070] snd_hda_codec_generic hdaudioC1D1:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.680074] snd_hda_codec_generic hdaudioC1D1:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.680077] snd_hda_codec_generic hdaudioC1D1:    mono: mono_out=0x0
[   17.680080] snd_hda_codec_generic hdaudioC1D1:    dig-out=0x5/0x0
[   17.680082] snd_hda_codec_generic hdaudioC1D1:    inputs:
[   17.736071] control 0:0:0:HDMI Jack:0 is already present
[   17.736145] snd_hda_codec_generic: probe of hdaudioC1D1 failed with error -16
[   17.736152] hdaudio hdaudioC1D1: Unable to bind the codec
[   17.762741] init: samba-ad-dc main process (738) terminated with status 1
[   17.769471] snd_hda_codec_hdmi: Unknown symbol snd_hdac_i915_register_notifier (err 0)
[   17.811270] snd_hda_codec_hdmi: Unknown symbol snd_hdac_i915_register_notifier (err 0)
[   17.828077] snd_hda_codec_generic hdaudioC1D2: autoconfig for ID b: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
[   17.828085] snd_hda_codec_generic hdaudioC1D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.828089] snd_hda_codec_generic hdaudioC1D2:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.828092] snd_hda_codec_generic hdaudioC1D2:    mono: mono_out=0x0
[   17.828095] snd_hda_codec_generic hdaudioC1D2:    dig-out=0x5/0x0
[   17.828098] snd_hda_codec_generic hdaudioC1D2:    inputs:
[   17.884084] control 0:0:0:HDMI Jack:0 is already present
[   17.884162] snd_hda_codec_generic: probe of hdaudioC1D2 failed with error -16
[   17.884170] hdaudio hdaudioC1D2: Unable to bind the codec
[   17.897723] snd_hda_codec_hdmi: Unknown symbol snd_hdac_i915_register_notifier (err 0)
[   17.915784] snd_hda_codec_hdmi: Unknown symbol snd_hdac_i915_register_notifier (err 0)
[   17.936079] snd_hda_codec_generic hdaudioC1D3: autoconfig for ID b: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
[   17.936088] snd_hda_codec_generic hdaudioC1D3:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.936092] snd_hda_codec_generic hdaudioC1D3:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.936095] snd_hda_codec_generic hdaudioC1D3:    mono: mono_out=0x0
[   17.936098] snd_hda_codec_generic hdaudioC1D3:    dig-out=0x5/0x0
[   17.936100] snd_hda_codec_generic hdaudioC1D3:    inputs:
[   17.992084] control 0:0:0:HDMI Jack:0 is already present
[   17.992159] snd_hda_codec_generic: probe of hdaudioC1D3 failed with error -16
[   17.992167] hdaudio hdaudioC1D3: Unable to bind the codec
[   17.992306] input: HDA NVidia HDMI as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input8
[   18.432427] init: nvidia-prime main process (963) terminated with status 127
--
[   29.285295] init: plymouth-upstart-bridge main process ended, respawning
[ 2403.123871] snd_hda_intel 0000:01:00.1: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.


```

---

### Post by Denis_Papathanasio on 2015-10-18
A more succinct explanation of my problem is that rebooting or shutting down and restarting switches the audio driver from oem-audio-hda-daily-lts-vivid-dkms (which is the only one that *does* work) to something else, oem-audio-hda-daily-lts-utopic-dkms, or oem-audio-hda-daily-dkms instead.

Also, it messes around with S/PDIF outputs, setting them all to mute, which I can undo easily enough through alsamixer, but it's annoying to have to do this every after a reboot.

I've been running mythbuntu on this equipment for several years, and this is the first time I've had such weird behavior after boots and cold startups.

Is there anything I can do to prevent it?

---

