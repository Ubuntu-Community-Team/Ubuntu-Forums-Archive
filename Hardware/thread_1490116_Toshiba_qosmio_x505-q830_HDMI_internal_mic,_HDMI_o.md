---
title: "Toshiba qosmio x505-q830 HDMI internal mic, HDMI out audio woes"
date: 2010-05-21
forum: Hardware
---

### Post by doogieanese on 2010-05-21
for starters: 
my **alsa-info.sh** output.
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Thu May 20 10:52:45 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      Qosmio X505


!!Kernel Information
!!------------------

Kernel release:    2.6.33-02063303-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

- 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0900000 irq 35
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xcdefc000 irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 05)
    Subsystem: 1179:ff50
--
01:00.1 0403: 10de:0be4 (rev a1)
    Subsystem: 1179:ff50


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-hda-intel: model=auto
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1
    model : auto,(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0
    single_cmd : N

!!Module: snd_hda_intel
    bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1
    model : auto,(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Conexant CX20583 (Pebble HSF)
Address: 0
Function Id: 0x1
Vendor Id: 0x14f15067
Subsystem Id: 0x1179ffd5
Revision Id: 0x100301
No Modem Function Group found
Default PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x10 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x34 0x34]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x31 0x31] [0x80 0x80] [0x31 0x31] [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17 0x18* 0x23 0x24
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x16 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x17 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a 0x1b 0x1d 0x1e*
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a 0x1b 0x1d 0x1e*
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x042140f0: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Green
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x04a190f0: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x2: EAPD
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x95a701f0: [Fixed] Mic at Int Top
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x921701f0: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x044511f0: [Jack] SPDIF Out at Ext Right
    Conn = Optical, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="Conexant Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x22 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x23 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x04, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x24 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono
Codec: Nvidia GT240 HDMI
Address: 0
Function Id: 0x1
Vendor Id: 0x10de000d
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=3
  Converter: stream=6, channel=0
  Digital: Enabled
  Digital category: 0x0
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
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GT240 HDMI
Address: 1
Function Id: 0x1
Vendor Id: 0x10de000d
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=7
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
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
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GT240 HDMI
Address: 2
Function Id: 0x1
Vendor Id: 0x10de000d
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=8
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
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
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
Codec: Nvidia GT240 HDMI
Address: 3
Function Id: 0x1
Vendor Id: 0x10de000d
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Control: name="IEC958 Playback Con Mask", index=3, device=0
  Control: name="IEC958 Playback Pro Mask", index=3, device=0
  Control: name="IEC958 Playback Default", index=3, device=0
  Control: name="IEC958 Playback Switch", index=3, device=0
  Device: name="NVIDIA HDMI", type="HDMI", device=9
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
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
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  0 May 20 19:29 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 32 May 20 19:29 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  4 May 20 19:29 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 36 May 20 19:29 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116, 37 May 20 19:29 /dev/snd/hwC1D1
crw-rw----+ 1 root audio 116, 38 May 20 19:29 /dev/snd/hwC1D2
crw-rw----+ 1 root audio 116, 39 May 20 19:29 /dev/snd/hwC1D3
crw-rw----+ 1 root audio 116, 24 May 20 19:35 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 May 20 19:31 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 17 May 20 19:29 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 51 May 20 19:29 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116, 55 May 20 19:29 /dev/snd/pcmC1D7p
crw-rw----+ 1 root audio 116, 56 May 20 19:29 /dev/snd/pcmC1D8p
crw-rw----+ 1 root audio 116, 57 May 20 19:29 /dev/snd/pcmC1D9p
crw-rw----+ 1 root audio 116,  1 May 20 19:29 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 May 20 19:29 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 May 20 19:29 .
drwxr-xr-x 3 root root 380 May 20 19:29 ..
lrwxrwxrwx 1 root root  12 May 20 19:29 pci-0000:00:1b.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 May 20 19:29 pci-0000:01:00.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xf0900000 irq 35'
  Mixer name    : 'Conexant CX20583 (Pebble HSF)'
  Components    : 'HDA:14f15067,1179ffd5,00100301'
  Controls      : 12
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 52 [70%] [-22.00dB] [on]
  Front Right: Playback 52 [70%] [-22.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic B',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic C',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic E',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic F',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 49 [61%] [-25.00dB] [on]
  Front Right: Capture 49 [61%] [-25.00dB] [on]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '0dB'

!!-------Mixer controls for card 1 [NVidia]

Card hw:1 'NVidia'/'HDA NVidia at 0xcdefc000 irq 17'
  Mixer name    : 'Nvidia GT240 HDMI'
  Components    : 'HDA:10de000d,10de0101,00100100'
  Controls      : 16
  Simple ctrls  : 4
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',3
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 74'
        comment.dbmin -7400
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 52
        value.1 52
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.3 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 '0dB'
        comment.item.1 '10dB'
        comment.item.2 '20dB'
        comment.item.3 '30dB'
        comment.item.4 '40dB'
        iface MIXER
        name 'Analog Mic Boost Capture Enum'
        value '0dB'
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 80'
        comment.dbmin -7400
        comment.dbmax 600
        iface MIXER
        name 'Capture Volume'
        value.0 49
        value.1 49
    }
    control.5 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
    }
    control.6 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.7 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.8 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
    control.10 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
    }
    control.11 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'Mic B'
        comment.item.1 'Mic C'
        comment.item.2 'Mic E'
        comment.item.3 'Mic F'
        iface MIXER
        name 'Capture Source'
        value 'Mic F'
    }
    control.12 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
    }
}
state.NVidia {
    control.1 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.2 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.3 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
    control.5 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 1
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.6 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 1
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.7 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        index 1
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.8 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        index 1
        value true
    }
    control.9 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 2
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.10 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 2
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.11 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        index 2
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.12 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        index 2
        value true
    }
    control.13 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 3
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.14 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 3
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.15 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        index 3
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        index 3
        value true
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
rfcomm
sco
bridge
stp
bnep
l2cap
vmnet
ppdev
parport_pc
vmblock
vsock
vmci
vmmon
snd_hda_codec_nvhdmi
snd_hda_codec_conexant
joydev
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_seq_dummy
snd_pcm
snd_seq_oss
snd_seq_midi
mmc_block
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
sdhci_pci
uvcvideo
sdhci
snd
btusb
videodev
v4l1_compat
soundcore
psmouse
v4l2_compat_ioctl32
atl1c
bluetooth
serio_raw
led_class
snd_page_alloc
video
nvidia
output
lp
parport
jfs
usb_storage
ohci1394
ahci
ieee1394


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x19 0x042140f0
0x1a 0x04a190f0
0x1b 0x400001f0
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x95a701f0
0x1f 0x921701f0
0x20 0x044511f0
0x22 0x400001f0
0x23 0x400001f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D1/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D1/driver_pin_configs:

/sys/class/sound/hwC1D1/user_pin_configs:

/sys/class/sound/hwC1D1/init_verbs:

/sys/class/sound/hwC1D2/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D2/driver_pin_configs:

/sys/class/sound/hwC1D2/user_pin_configs:

/sys/class/sound/hwC1D2/init_verbs:

/sys/class/sound/hwC1D3/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC1D3/driver_pin_configs:

/sys/class/sound/hwC1D3/user_pin_configs:

/sys/class/sound/hwC1D3/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   13.974226]   alloc kstat_irqs on node -1
[   13.974233] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.974359]   alloc irq_desc for 35 on node -1
[   13.974362]   alloc kstat_irqs on node -1
[   13.974377] HDA Intel 0000:00:1b.0: irq 35 for MSI/MSI-X
[   13.974441] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.192472]   alloc irq_desc for 17 on node -1
[   14.192474]   alloc kstat_irqs on node -1
[   14.192480] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.192481] hda_intel: Disable MSI for Nvidia chipset
[   14.192631] HDA Intel 0000:01:00.1: setting latency timer to 64
[   20.831496]   alloc irq_desc for 36 on node -1
--
[   26.135884] bridge-eth0: attached
[   26.286271] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   26.353196] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   27.259550] /dev/vmnet: open called by PID 1552 (vmnet-dhcpd)
--
[   27.567337] /dev/vmnet: port on hub 8 successfully opened
[   28.297573] HDMI: detected monitor HP w2338h
[   28.297577]    at connection type HDMI
[   28.297582] HDMI: available speakers: FL/FR
[   28.297590] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 
[   28.512464] Bluetooth: L2CAP ver 2.14
--
[   31.175160] eth0: no IPv6 routers present
[   36.050455] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   37.840802] vmnet1: no IPv6 routers present


```**my alsa-base.conf**
```


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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
#options snd-hda-intel model=toshiba
#options snd-hda-intel model=olpc-xo-1_5
options snd-hda-intel model=auto
#options snd-hda-intel model=dell-vostro
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

```**Things i have tried**:
I have complied and installed ALSA 1.0.21 through 1.0.23(currently ~.23)
I have also gone to kernel~.33
I have tried other options in the .conf file to get the mic to work

all channels un-muted in alsamixer any where from 0-40 db boost.
 any option but auto in .conf give no sound output at all.
[B]
Internal Mic[/B]:
In none of these versions am i able to use/see/select the internal mic in G-V-C.
at one point on a late night last week, I had the ability to hook in an external mic (well head-phones really as my external mic was overdriving the port). I think this was in 1.0.22 with kernel .33 , I changed something, can't remember what, it broke again and i gave up and went to sleep and now can't remember. I have not had external ports since. It all worked in windows 7 native, so i'm relatively sure its not hardware.

**HDMI**

there was a bug fix/work around for the hdmi that i meant to try from a  myth user that i found when i started this saga three weeks ago, I can't  find it now.only with 1.0.23 was i able to see the HDMI in G-V-C.

I have done a lot of searching of google and of the ubuntu forum, any further asistance would be appreciated.

not a computer newb;smarter than your average bear. not exactly a linux newb, but deffinitly not a 1337.

thanks in advance

---

### Post by doogieanese on 2010-05-22
hdmi issue solved.

note:
this only works if you see four outputs in alsamixer for the nvidia card.
For me this took running alsaconf which required a install of alsa from scratch to get alsaconf, which Ubuntu leaves out as "unnecessary"

good link for 10.04 alsa 1.0.23 build how to (should work for other versions):
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)


after alsa is seeing the card and the four outputs, unmute them in alsamixer, and add:
```

options snd-hda-intel probe_mask=0xffff,0xfff2

```
reboot

thanks to this thread for the alsa-base.conf line:
[http://xbmc.org/forum/showthread.php...129#post502129]("http://xbmc.org/forum/showthread.php?p=502129#post502129")


Still looking for the internal mic fix. Any help out there? There always seems to be a ton of internal mic problems. so i remain hopeful something useful comes along.

---

