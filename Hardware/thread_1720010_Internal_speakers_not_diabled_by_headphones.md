---
title: "Internal speakers not diabled by headphones"
date: 2011-04-02
forum: Hardware
---

### Post by jchiso on 2011-04-02
I've searched at great length and tried numerous things, but I continue to get sound from my internal speakers while using the headphone jack on my Acer 5253 notebook with Maverick.  I tried installing gnome-alsa-mixer, but nothing appears for headphone control.  I've set options to 'auto', 'laptop', 'acer' and a few others, but nothing seems to work.  It's not a hardware problem, because the jack behaves as expected in Windows 7.

Any help would be greatly appreciated ...

---

### Post by lidex on 2011-04-02
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by jchiso on 2011-04-03
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Apr  3 14:04:53 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Acer
Product Name:      Aspire 5253
Product Version:   V1.02


!!Kernel Information
!!------------------

Kernel release:    2.6.35-28-generic
Operating System:  GNU/Linux
Architecture:      i686
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

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0x90544000 irq 43
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0x90540000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:01.1 Audio device: ATI Technologies Inc Device 1314
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:01.1 0403: 1002:1314
	Subsystem: 1025:0520
--
00:14.2 0403: 1002:4383 (rev 40)
	Subsystem: 1025:0520


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=acer


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : laptop,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : laptop,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
Function Id: 0x1
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="ATI HDMI", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Codec: Conexant ID 5068
Address: 0
Function Id: 0x1
Vendor Id: 0x14f15068
Subsystem Id: 0x10250520
Revision Id: 0x100302
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
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="HDA Generic", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x4a 0x4a]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3c 0x3c]
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
  Control: name="Capture Source", index=0, device=0
  Control: name="Mic Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic 1 Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Device: name="HDA Generic", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x50 0x50] [0x4a 0x4a] [0x4a 0x4a]
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
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
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
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
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
  Amp-Out vals:  [0x04 0x04]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x04 0x04]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a 0x1b* 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x04211040: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x95a70120: [Fixed] Mic at Int Top
    Conn = Analog, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x0:
  Pin Default 0x04a11030: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
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
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x0:
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x92170110: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
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
  Pin-ctls: 0x00:
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
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  6 Apr  2 15:52 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 10 Apr  2 15:52 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  5 Apr  2 15:52 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  9 Apr  2 15:52 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  4 Apr  2 16:24 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  8 Apr  2 16:42 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  7 Apr  3 09:58 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  3 Apr  2 16:24 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Apr  2 15:52 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Apr  2 15:52 .
drwxr-xr-x 3 root root 240 Apr  2 16:24 ..
lrwxrwxrwx 1 root root  12 Apr  2 15:52 pci-0000:00:01.1 -> ../controlC0
lrwxrwxrwx 1 root root  12 Apr  2 15:52 pci-0000:00:14.2 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Generic]

Card hw:0 'Generic'/'HD-Audio Generic at 0x90544000 irq 43'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100200'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [SB]

Card hw:1 'SB'/'HDA ATI SB at 0x90540000 irq 16'
  Mixer name	: 'Conexant ID 5068'
  Components	: 'HDA:14f15068,10250520,00100302'
  Controls      : 6
  Simple ctrls  : 4
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 0 [0%] [-74.00dB] [on]
  Front Right: Capture 0 [0%] [-74.00dB] [on]
Simple mixer control 'Mic 1',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [off]
  Front Right: Capture 80 [100%] [6.00dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Generic {
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
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
}
state.SB {
	control.1 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Mic 1'
		iface MIXER
		name 'Capture Source'
		value Mic
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'Mic Capture Volume'
		value.0 0
		value.1 0
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'Mic 1 Capture Volume'
		value.0 80
		value.1 80
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 74'
		comment.dbmin -7400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 74
		value.1 74
	}
	control.6 {
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
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_seq_device
aes_i586
aes_generic
joydev
binfmt_misc
ir_lirc_codec
ir_sony_decoder
ir_jvc_decoder
ir_rc6_decoder
ir_rc5_decoder
ir_nec_decoder
streamzap
ir_core
lirc_dev
parport_pc
ppdev
snd_hda_codec_atihdmi
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
arc4
ath9k
mac80211
snd_timer
ath9k_common
fglrx
ath9k_hw
ath
uvcvideo
cfg80211
videodev
snd
v4l1_compat
psmouse
led_class
i2c_piix4
soundcore
agpgart
serio_raw
snd_page_alloc
video
output
lp
parport
usb_storage
ahci
libahci
dm_raid45
xor


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x19 0x04211040
0x1a 0x95a70120
0x1b 0x04a11030
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x400001f0
0x1f 0x92170110
0x20 0x400001f0
0x22 0x400001f0
0x23 0x400001f0

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   19.899467] phy0: Atheros AR9287 Rev:2 mem=0xf88e0000, irq=19
[   19.977222] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   19.977299]   alloc irq_desc for 43 on node -1
[   19.977303]   alloc kstat_irqs on node -1
[   19.977320] HDA Intel 0000:00:01.1: irq 43 for MSI/MSI-X
[   19.977355] HDA Intel 0000:00:01.1: setting latency timer to 64
[   20.003829] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.003910] HDA Intel 0000:00:14.2: setting latency timer to 64
[   20.016263] elantech: assuming hardware version 2, firmware version 4.2.19
--
[   23.404876] [fglrx] Reserved FB block: Unshared offset:fff4000, size:c000 
[   27.323532] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   27.325720] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
--
[30775.424117] ehci_hcd 0000:00:13.2: PCI INT B disabled
[30775.512064] HDA Intel 0000:00:01.1: PCI INT B disabled
[30775.512104] ACPI handle has no context!
[30775.512549] HDA Intel 0000:00:14.2: PCI INT A disabled
[30775.528512] PM: suspend of drv:HDA Intel dev:0000:00:01.1 complete after 117.228 msecs
[30775.528525] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 117.289 msecs
[30775.569116] sd 0:0:0:0: [sda] Stopping disk
--
[30776.433553] fglrx_pci 0000:00:01.0: setting latency timer to 64
[30776.433616] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[30776.433626] HDA Intel 0000:00:01.1: setting latency timer to 64
[30776.433682] HDA Intel 0000:00:01.1: irq 43 for MSI/MSI-X
[30776.433727] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
--
[30776.436631] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[30776.436684] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[30776.436765] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19


```

---

### Post by lidex on 2011-04-03
I would remove that acer model switch from alsa-base.conf then update your alsa-modules and rerun the info script.

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by jchiso on 2011-04-03
It didn't work.  Now I don't get sound through the headphones at all.  The (Gnome) alsa mixer now shows an additional control for "Beep" as well as options for 'Mic C', 'Mic D', 'Mic E', 'Mic F', and 'Analog Mic Boost'...

---

### Post by hreichgott on 2011-04-04
I am having the same problem on an Acer 5253.
Also, plugging in an external mic does not disable the internal mic. This is extremely annoying since I need to use my computer for audio production, but now cannot. I posted about this but got no response 
([http://ubuntuforums.org/showthread.php?t=1713697](http://ubuntuforums.org/showthread.php?t=1713697))

This is my alsa-project output. I wonder if the two sound cards are the problem? If so, is there a way to turn one of them off?
```
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Mon Apr  4 14:30:30 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Acer
Product Name:      Aspire 5253
Product Version:   V1.02


!!Kernel Information
!!------------------

Kernel release:    2.6.35-28-generic
Operating System:  GNU/Linux
Architecture:      i686
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

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0x90544000 irq 43
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0x90540000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:01.1 Audio device: ATI Technologies Inc Device 1314
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:01.1 0403: 1002:1314
    Subsystem: 1025:0520
--
00:14.2 0403: 1002:4383 (rev 40)
    Subsystem: 1025:0520


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N

!!Module: snd_hda_intel
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
Function Id: 0x1
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="ATI HDMI", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Codec: Conexant ID 5068
Address: 0
Function Id: 0x1
Vendor Id: 0x14f15068
Subsystem Id: 0x10250520
Revision Id: 0x100302
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
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="HDA Generic", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3d 0x3d]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3c 0x3c]
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
  Control: name="Capture Source", index=0, device=0
  Control: name="Mic Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic 1 Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Device: name="HDA Generic", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4b 0x4b] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
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
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
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
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
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
  Amp-Out vals:  [0x04 0x04]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x04 0x04]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a 0x1b* 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x04211040: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x95a70120: [Fixed] Mic at Int Top
    Conn = Analog, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x0:
  Pin Default 0x04a11030: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
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
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x0:
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x92170110: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
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
  Pin-ctls: 0x00:
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
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  6 Apr  4 10:25 /dev/snd/controlC0
crw-rw----  1 root audio 116, 10 Apr  4 10:25 /dev/snd/controlC1
crw-rw----  1 root audio 116,  5 Apr  4 10:25 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  9 Apr  4 10:25 /dev/snd/hwC1D0
crw-rw----  1 root audio 116,  4 Apr  4 10:27 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116,  8 Apr  4 10:27 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116,  7 Apr  4 10:28 /dev/snd/pcmC1D0p
crw-rw----  1 root audio 116,  3 Apr  4 10:25 /dev/snd/seq
crw-rw----  1 root audio 116,  2 Apr  4 10:25 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Apr  4 10:25 .
drwxr-xr-x 3 root root 240 Apr  4 10:25 ..
lrwxrwxrwx 1 root root  12 Apr  4 10:25 pci-0000:00:01.1 -> ../controlC0
lrwxrwxrwx 1 root root  12 Apr  4 10:25 pci-0000:00:14.2 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Generic]

Card hw:0 'Generic'/'HD-Audio Generic at 0x90544000 irq 43'
  Mixer name    : 'ATI R6xx HDMI'
  Components    : 'HDA:1002aa01,00aa0100,00100200'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [SB]

Card hw:1 'SB'/'HDA ATI SB at 0x90540000 irq 16'
  Mixer name    : 'Conexant ID 5068'
  Components    : 'HDA:14f15068,10250520,00100302'
  Controls      : 6
  Simple ctrls  : 4
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 61 [82%] [-13.00dB] [on]
  Front Right: Playback 61 [82%] [-13.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 252 [99%] [0.60dB]
  Front Right: Playback 252 [99%] [0.60dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 75 [94%] [1.00dB] [on]
  Front Right: Capture 75 [94%] [1.00dB] [on]
Simple mixer control 'Mic 1',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 74 [92%] [0.00dB] [off]
  Front Right: Capture 74 [92%] [0.00dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Generic {
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
}
state.SB {
    control.1 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Mic 1'
        iface MIXER
        name 'Capture Source'
        value Mic
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 80'
        comment.dbmin -7400
        comment.dbmax 600
        iface MIXER
        name 'Mic Capture Volume'
        value.0 75
        value.1 75
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 80'
        comment.dbmin -7400
        comment.dbmax 600
        iface MIXER
        name 'Mic 1 Capture Volume'
        value.0 74
        value.1 74
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Master Playback Switch'
        value.0 true
        value.1 true
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 74'
        comment.dbmin -7400
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 61
        value.1 61
    }
    control.6 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 252
        value.1 252
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
michael_mic
arc4
fglrx
joydev
agpgart
binfmt_misc
parport_pc
ppdev
snd_hda_codec_atihdmi
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
lib80211_crypt_tkip
snd_seq_device
uvcvideo
wl
videodev
snd
v4l1_compat
psmouse
soundcore
snd_page_alloc
lib80211
serio_raw
i2c_piix4
video
output
lp
parport
ahci
libahci
usb_storage


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x19 0x04211040
0x1a 0x95a70120
0x1b 0x04a11030
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x400001f0
0x1f 0x92170110
0x20 0x400001f0
0x22 0x400001f0
0x23 0x400001f0

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   14.486754] type=1400 audit(1301927134.120:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=682 comm="apparmor_parser"
[   14.683716] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   14.683799]   alloc irq_desc for 43 on node -1
[   14.683803]   alloc kstat_irqs on node -1
[   14.683820] HDA Intel 0000:00:01.1: irq 43 for MSI/MSI-X
[   14.683856] HDA Intel 0000:00:01.1: setting latency timer to 64
[   14.744571] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.744729] HDA Intel 0000:00:14.2: setting latency timer to 64
[   14.784282] type=1400 audit(1301927134.416:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=832 comm="apparmor_parser"
--
[   16.998397] [fglrx] Reserved FB block: Unshared offset:fff4000, size:c000 
[   20.989424] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   21.193239] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=600
```

---

### Post by lidex on 2011-04-04
OK. I'm going blind but I think making progress. These acer machines (5253 and perhaps others) utilize the conexant ID 5068 codec. This codec has had limited support in alsa, however v. 1.0.24 includes a long list of changes and should provide full functionality. Remove any alsa-base modifications, alsa backports or alsa modules from the ppa. Next follow the alsa-upgrade link in my sig and use the script Temüjin is maintaining there. Read the first post carefully before proceeding.

For those interested, full alsa changelog is here:
[http://www.alsa-project.org/main/index.php/Detailed_HDA_changes_v1.0.23_v1.0.24](http://www.alsa-project.org/main/index.php/Detailed_HDA_changes_v1.0.23_v1.0.24)

---

### Post by Marcelush on 2011-04-05
When i had a problem like that on acer aspire 5720z i just unistalled my audio driver , reebot sistem , and then reinstall driver. Any problem haven't occured again.

---

### Post by jchiso on 2011-04-07
> **lidex said:**
> ... Remove any alsa-base modifications, alsa backports or alsa modules from the ppa ... 

How do I go about doing this?

---

### Post by lidex on 2011-04-09
> **jchiso said:**
> How do I go about doing this?

Post these outputs please:
```
dpkg -l | grep "alsa"
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by jchiso on 2011-04-09
```
ii  alsa-base                                                        1.0.23+dfsg-1ubuntu4                       ALSA driver configuration files
ii  alsa-utils                                                       1.0.23-2ubuntu3.4                          Utilities for configuring and using ALSA
ii  bluez-alsa                                                       4.69-0ubuntu2                              Bluetooth audio support
ii  gnome-alsamixer                                                  0.9.7~cvs.20060916.ds.1-2                  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                               0.10.30-2                                  GStreamer plugin for ALSA
ii  libsox-fmt-alsa                                                  14.3.1-1build1                             SoX alsa format I/O library
ii  linux-alsa-driver-modules-2.6.35-28-generic                      2.6.35-28.201104071603                     Ubuntu-supplied Linux modules for version 2.6.35-28-generic ALSA snapshots

```


```
ii  alsa-base                                                        1.0.23+dfsg-1ubuntu4                       ALSA driver configuration files
ii  alsa-utils                                                       1.0.23-2ubuntu3.4                          Utilities for configuring and using ALSA
ii  bluez-alsa                                                       4.69-0ubuntu2                              Bluetooth audio support
ii  gnome-alsamixer                                                  0.9.7~cvs.20060916.ds.1-2                  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                               0.10.30-2                                  GStreamer plugin for ALSA
ii  libsox-fmt-alsa                                                  14.3.1-1build1                             SoX alsa format I/O library
ii  linux-alsa-driver-modules-2.6.35-28-generic                      2.6.35-28.201104071603                     Ubuntu-supplied Linux modules for version 2.6.35-28-generic ALSA snapshots
owner@Aspire5253:~$ ^C
owner@Aspire5253:~$ cat /etc/modprobe.d/alsa-base.conf
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

### Post by lidex on 2011-04-10
OK. Open software sources:
```
gksu software-properties-gtk

```
On the "Other Software" tab, disable the audio-dev ppa. Close that out. In the terminal:
```
sudo apt-get remove linux-alsa-driver-modules-2.6.35-28-generic
```
Reboot and follow the link to the alsa-upgrade script.

---

### Post by jchiso on 2011-04-10
> **lidex said:**
> OK. Open software sources:
```
gksu software-properties-gtk

```

```
sudo apt-get remove linux-alsa-driver-modules-2.6.35-28-generic
```
Reboot and follow the link to the alsa-upgrade script.

I executed these commands and the system went back to simultaneously producing sound via speakers and headphones.  Then I ran the script and now it's speakers-only ...

---

### Post by bejurne on 2011-04-10
I have the same problem on an Ideapad s205. It has the same soundchip according to lspci:

```
00:01.1 Audio device: ATI Technologies Inc Device 1314

```

Alsamixer shows no volume levels at all. And the gnome-volume-control does not seem to recognize that there is a headphone output. It only shows an option for switching between normal and HDMI output.


Output from the alsa-script:
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Apr 10 20:42:58 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      10382LG
Product Version:   Ideapad S205


!!Kernel Information
!!------------------

Kernel release:    2.6.35-28-generic
Operating System:  GNU/Linux
Architecture:      i686
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

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0244000 irq 43
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf0240000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:01.1 Audio device: ATI Technologies Inc Device 1314
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:01.1 0403: 1002:1314
	Subsystem: 17aa:397b
--
00:14.2 0403: 1002:4383 (rev 40)
	Subsystem: 17aa:397b


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
Function Id: 0x1
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="ATI HDMI", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Codec: Conexant ID 506e
Address: 0
Function Id: 0x1
Vendor Id: 0x14f1506e
Subsystem Id: 0x17aa6005
Revision Id: 0x100000
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
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="HDA Generic", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Control: name="Capture Source", index=0, device=0
  Control: name="Mic Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Mic 1 Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="HDA Generic", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x06 0x06] [0x4a 0x4a] [0x00 0x00] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 4
     0x17 0x18 0x23* 0x24
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x16 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x17 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x04 0x04]
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a 0x1b* 0x1d 0x1e
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x02211040: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x0:
  Pin Default 0x04a11030: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x0:
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x92170110: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
Node 0x22 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x23 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x04, stepsize=0x2f, mute=0
  Amp-In vals:  [0x04 0x04]
  Pincap 0x00000020: IN
  Pin Default 0x95a60120: [Fixed] Mic at Int Top
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
Node 0x24 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  6 Apr 10 21:07 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 10 Apr 10 21:07 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  5 Apr 10 21:07 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  9 Apr 10 21:07 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  4 Apr 10 21:11 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  8 Apr 10 21:33 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  7 Apr 10 21:13 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  3 Apr 10 21:07 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Apr 10 21:07 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Apr 10 21:07 .
drwxr-xr-x 3 root root 240 Apr 10 21:07 ..
lrwxrwxrwx 1 root root  12 Apr 10 21:07 pci-0000:00:01.1 -> ../controlC0
lrwxrwxrwx 1 root root  12 Apr 10 21:07 pci-0000:00:14.2 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Generic]

Card hw:0 'Generic'/'HD-Audio Generic at 0xf0244000 irq 43'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100200'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]

!!-------Mixer controls for card 1 [SB]

Card hw:1 'SB'/'HDA ATI SB at 0xf0240000 irq 16'
  Mixer name	: 'Conexant ID 506e'
  Components	: 'HDA:14f1506e,17aa6005,00100000'
  Controls      : 6
  Simple ctrls  : 4
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 60 [81%] [-14.00dB] [on]
  Front Right: Playback 60 [81%] [-14.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 0 [0%] [-74.00dB] [on]
  Front Right: Capture 0 [0%] [-74.00dB] [on]
Simple mixer control 'Mic 1',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 6 [8%] [-68.00dB] [off]
  Front Right: Capture 6 [8%] [-68.00dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Generic {
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
		value false
	}
}
state.SB {
	control.1 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Mic 1'
		iface MIXER
		name 'Capture Source'
		value Mic
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'Mic Capture Volume'
		value.0 0
		value.1 0
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 80'
		comment.dbmin -7400
		comment.dbmax 600
		iface MIXER
		name 'Mic 1 Capture Volume'
		value.0 6
		value.1 6
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 74'
		comment.dbmin -7400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 60
		value.1 60
	}
	control.6 {
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
--endcollapse--


!!All Loaded Modules
!!------------------

Module
aes_i586
aes_generic
snd_hda_codec_atihdmi
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
arc4
snd_rawmidi
joydev
snd_seq_midi_event
ath9k
snd_seq
ath9k_common
ath9k_hw
snd_timer
snd_seq_device
ath
mac80211
snd
fglrx
btusb
uvcvideo
videodev
video
soundcore
cfg80211
output
v4l1_compat
snd_page_alloc
bluetooth
lp
acer_wmi
parport
psmouse
i2c_piix4
agpgart
led_class
serio_raw
ahci
r8169
mii
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x19 0x02211040
0x1a 0x400001f0
0x1b 0x04a11030
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x400001f0
0x1f 0x92170110
0x20 0x400001f0
0x22 0x400001f0
0x23 0x95a60120

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[    8.255753]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.392117] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    8.392197]   alloc irq_desc for 43 on node -1
[    8.392201]   alloc kstat_irqs on node -1
[    8.392219] HDA Intel 0000:00:01.1: irq 43 for MSI/MSI-X
[    8.392256] HDA Intel 0000:00:01.1: setting latency timer to 64
[    8.486217] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.982998] r8169 0000:02:00.0: eth0: link down
--
[   38.113031] wlan0: no IPv6 routers present
[  237.312630] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  334.252846] gnome-power-man[1404]: segfault at 284 ip 00613f4b sp bf971ab0 error 4 in libgtk-x11-2.0.so.0.2200.0[51f000+3c8000]
--
[ 1683.118490] EXT4-fs (sda5): re-mounted. Opts: commit=0
[ 5743.760014] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x001f000a
[ 5744.764013] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x001f000a


```



I am bit hesitant to executing that script since there seems no easy way to undo it. And if I understand jchiso right, it did not work for him. Any other ideas?

---

### Post by jchiso on 2011-04-10
> **bejurne said:**
> ... I am bit hesitant to executing that script since there seems no easy way to undo it. And if I understand jchiso right, it did not work for him. Any other ideas?

I did not realize there's no easy way to undo it, but no, it did not work.  I also had to add the line about "pulse.conf" to the alsa.conf file to get sound to work in Firefox.

---

### Post by jchiso on 2011-04-15
Any other thougts at all on this?  I tried running Lucid from a thumbdrive and it has the same problem.  Pretty much makes this notebook useless as a mobile Ubuntu platform ...

---

### Post by lidex on 2011-04-17
> **jchiso said:**
> Any other thougts at all on this?  I tried running Lucid from a thumbdrive and it has the same problem.  Pretty much makes this notebook useless as a mobile Ubuntu platform ...

What are your vitals now?
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
```
dpkg -l | grep "alsa"
```

---

### Post by jchiso on 2011-04-17
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun Apr 17 21:47:31 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Acer
Product Name:      Aspire 5253
Product Version:   V1.02


!!Kernel Information
!!------------------

Kernel release:    2.6.35-28-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


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

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0x90544000 irq 43
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0x90540000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:01.1 Audio device: ATI Technologies Inc Device 1314
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:01.1 0403: 1002:1314
	Subsystem: 1025:0520
--
00:14.2 0403: 1002:4383 (rev 40)
	Subsystem: 1025:0520


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x02
Codec: Conexant CX20584
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x14f15068
Subsystem Id: 0x10250520
Revision Id: 0x100302
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
  Amp-Out vals:  [0x4a 0x48]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3c 0x3c]
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
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0xd0 0xd0] [0x80 0x80] [0xd0 0xd0] [0x80 0x80]
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
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
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
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
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
     0x1a* 0x1b 0x1d 0x1e
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x04211040: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x95a70120: [Fixed] Mic at Int Top
    Conn = Analog, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x2: EAPD
  Pin Default 0x04a11030: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
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
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x92170110: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
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
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
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
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  4 Apr 15 20:46 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  8 Apr 15 20:46 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  3 Apr 15 20:46 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  7 Apr 15 20:46 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  2 Apr 15 20:46 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  6 Apr 15 20:46 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  5 Apr 17 14:45 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  1 Apr 15 20:45 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Apr 15 20:45 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Apr 15 20:46 .
drwxr-xr-x 3 root root 240 Apr 15 20:46 ..
lrwxrwxrwx 1 root root  12 Apr 15 20:46 pci-0000:00:01.1 -> ../controlC0
lrwxrwxrwx 1 root root  12 Apr 15 20:46 pci-0000:00:14.2 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Generic]

Card hw:0 'Generic'/'HD-Audio Generic at 0x90544000 irq 43'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100200'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [SB]

Card hw:1 'SB'/'HDA ATI SB at 0x90540000 irq 16'
  Mixer name	: 'Conexant CX20584'
  Components	: 'HDA:14f15068,10250520,00100302'
  Controls      : 9
  Simple ctrls  : 9
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 72 [97%] [-2.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 252 [99%] [0.60dB]
Simple mixer control 'Mic B',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
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
  Mono: Capture [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 7 [100%] [0.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [off]
  Front Right: Capture 80 [100%] [6.00dB] [off]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '0dB'


!!Alsactl output
!!-------------

--startcollapse--
state.Generic {
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
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
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
}
state.SB {
	control.1 {
		iface MIXER
		name 'Master Playback Volume'
		value.0 74
		value.1 72
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 74'
			dbmin -7400
			dbmax 0
			dbvalue.0 0
			dbvalue.1 -200
		}
	}
	control.2 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'Analog Mic Boost Capture Enum'
		value '0dB'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 '0dB'
			item.1 '10dB'
			item.2 '20dB'
			item.3 '30dB'
			item.4 '40dB'
		}
	}
	control.4 {
		iface MIXER
		name 'Capture Volume'
		value.0 80
		value.1 80
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 80'
			dbmin -7400
			dbmax 600
			dbvalue.0 600
			dbvalue.1 600
		}
	}
	control.5 {
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.6 {
		iface MIXER
		name 'Capture Source'
		value 'Mic B'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Mic B'
			item.1 'Mic C'
			item.2 'Mic E'
			item.3 'Mic F'
		}
	}
	control.7 {
		iface MIXER
		name 'Beep Playback Volume'
		value 7
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 7'
			dbmin -2800
			dbmax 0
			dbvalue.0 0
		}
	}
	control.8 {
		iface MIXER
		name 'Beep Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.9 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 252
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 0
			dbvalue.1 -60
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
aes_i586
aes_generic
binfmt_misc
ir_lirc_codec
ir_sony_decoder
ir_jvc_decoder
ir_rc6_decoder
ir_rc5_decoder
ir_nec_decoder
streamzap
ir_core
lirc_dev
parport_pc
ppdev
joydev
snd_hda_codec_conexant
snd_hda_codec_hdmi
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
arc4
snd_timer
snd_seq_device
ath9k
mac80211
ath9k_common
ath9k_hw
fglrx
snd
ath
uvcvideo
soundcore
snd_page_alloc
videodev
cfg80211
v4l1_compat
psmouse
agpgart
serio_raw
i2c_piix4
led_class
lp
video
output
parport
ahci
libahci
usb_storage
dm_raid45
xor


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x19 0x04211040
0x1a 0x95a70120
0x1b 0x04a11030
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x400001f0
0x1f 0x92170110
0x20 0x400001f0
0x22 0x400001f0
0x23 0x400001f0

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   22.536046] elantech: retrying ps2 command 0xf8 (1).
[   22.542952] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   22.543025]   alloc irq_desc for 43 on node -1
[   22.543029]   alloc kstat_irqs on node -1
[   22.543046] HDA Intel 0000:00:01.1: irq 43 for MSI/MSI-X
[   22.543083] HDA Intel 0000:00:01.1: setting latency timer to 64
[   22.612377] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.612451] HDA Intel 0000:00:14.2: setting latency timer to 64
[   22.764241] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input7
[   23.105259] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input8
--
[   25.578704] [fglrx] Reserved FB block: Unshared offset:fff4000, size:c000 
[   28.486660] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   29.246896] EXT4-fs (sdb7): re-mounted. Opts: errors=remount-ro,commit=0
--
[  545.068547] ehci_hcd 0000:00:13.2: PCI INT B disabled
[  545.156552] HDA Intel 0000:00:01.1: PCI INT B disabled
[  545.156592] ACPI handle has no context!
[  545.157553] HDA Intel 0000:00:14.2: PCI INT A disabled
[  545.176015] PM: suspend of drv:HDA Intel dev:0000:00:01.1 complete after 123.879 msecs
[  545.176029] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 123.989 msecs
[  545.238039] [fglrx] Suspending fglrx in kernel completed.
--
[  545.861319] fglrx_pci 0000:00:01.0: setting latency timer to 64
[  545.861555] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  545.861563] HDA Intel 0000:00:01.1: setting latency timer to 64
[  545.861609] HDA Intel 0000:00:01.1: irq 43 for MSI/MSI-X
[  545.861653] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
--
[  545.861811] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  545.861835] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  545.861895] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
--
[ 4182.101052] ohci_hcd 0000:00:12.0: PCI INT A disabled
[ 4182.101127] HDA Intel 0000:00:01.1: PCI INT B disabled
[ 4182.101169] [fglrx] IRQ 44 Disabled
--
[ 4182.120087] ehci_hcd 0000:00:13.2: PCI INT B disabled
[ 4182.204937] HDA Intel 0000:00:14.2: PCI INT A disabled
[ 4182.224014] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 123.360 msecs
[ 4182.284235] [fglrx] Suspending fglrx in kernel completed.
--
[ 4182.933146] fglrx_pci 0000:00:01.0: setting latency timer to 64
[ 4182.933262] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 4182.933272] HDA Intel 0000:00:01.1: setting latency timer to 64
[ 4182.933329] HDA Intel 0000:00:01.1: irq 43 for MSI/MSI-X
[ 4182.933378] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
--
[ 4182.933562] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 4182.933585] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4182.933645] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
--
[23094.781464] ohci_hcd 0000:00:12.0: PCI INT A disabled
[23094.781514] HDA Intel 0000:00:01.1: PCI INT B disabled
[23094.781553] ACPI handle has no context!
--
[23094.796599] ehci_hcd 0000:00:13.2: PCI INT B disabled
[23094.888419] HDA Intel 0000:00:14.2: PCI INT A disabled
[23094.904015] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 122.709 msecs
[23094.966518] [fglrx] Suspending fglrx in kernel completed.
--
[23095.617116] fglrx_pci 0000:00:01.0: setting latency timer to 64
[23095.617207] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[23095.617216] HDA Intel 0000:00:01.1: setting latency timer to 64
[23095.617270] HDA Intel 0000:00:01.1: irq 43 for MSI/MSI-X
[23095.617317] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
--
[23095.617514] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[23095.617538] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[23095.617598] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19


```

```
ii  alsa-base                                                        1.0.23+dfsg-1ubuntu4                       ALSA driver configuration files
ii  alsa-firmware                                                    1.0.20-0medibuntu4.2                       Contains firmware for ALSA devices - Medibuntu package
ii  alsa-firmware-loaders                                            1.0.23-3ubuntu1                            ALSA software loaders for specific hardware
ii  alsa-oss                                                         1.0.17-4                                   ALSA wrapper for OSS applications
ii  alsa-source                                                      1.0.23+dfsg-1ubuntu4                       ALSA driver sources
ii  alsa-tools                                                       1.0.23-3ubuntu1                            Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                                                   1.0.23-3ubuntu1                            GUI based ALSA utilities for specific hardware
ii  alsa-utils                                                       1.0.23-2ubuntu3.4                          Utilities for configuring and using ALSA
ii  bluez-alsa                                                       4.69-0ubuntu2                              Bluetooth audio support
ii  gnome-alsamixer                                                  0.9.7~cvs.20060916.ds.1-2                  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                               0.10.30-2                                  GStreamer plugin for ALSA
ii  libsox-fmt-alsa                                                  14.3.1-1build1                             SoX alsa format I/O library
rc  linux-alsa-driver-modules-2.6.35-28-generic                      2.6.35-28.201104071603                     Ubuntu-supplied Linux modules for version 2.6.35-28-generic ALSA snapshots

```

---

### Post by lidex on 2011-04-17
You've got the snapshot (alsa-modules) installed. That will override  the script. Try removing it.

---

### Post by jchiso on 2011-04-17
> **lidex said:**
> You've got the snapshot (alsa-modules) installed. That will override  the script. Try removing it.

How do I go about doing that without getting further undesired results?

---

### Post by Yellow Pasque on 2011-04-17
> **jchiso said:**
> How do I go about doing that without getting further undesired results?
You would remove linux-alsa-driver-modules-2.6.35-28-generic and run the script with -i again.

---

### Post by jchiso on 2011-04-18
> **Temüjin said:**
> You would remove linux-alsa-driver-modules-2.6.35-28-generic and run the script with -i again.

It says the modules are not installed ...

---

### Post by lidex on 2011-04-18
> **jchiso said:**
> It says the modules are not installed ...
I think the "rc" (dpkg) shows a remaining configuration even though the package was removed. Use synaptic and select 'Status' on the bottom-left, then 'Not installed (residual config)' on the top-left and mark for complete removal.

---

### Post by jchiso on 2011-04-18
> **lidex said:**
> I think the "rc" (dpkg) shows a remaining configuration even though the package was removed. Use synaptic and select 'Status' on the bottom-left, then 'Not installed (residual config)' on the top-left and mark for complete removal.

> **Temüjin said:**
> You would remove linux-alsa-driver-modules-2.6.35-28-generic and run the script with -i again.

Well, I executed these steps, but the functionality hasn't changed; audio through the speakers, none through headphones ...

---

### Post by lidex on 2011-04-18
> **jchiso said:**
> Well, I executed these steps, but the functionality hasn't changed; audio through the speakers, none through headphones ...

What is amixer now:
```
amixer
```

---

### Post by jchiso on 2011-04-18
> **lidex said:**
> What is amixer now:
```
amixer
```

```
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
```

And for what it's worth, I don't have audio in YouTube videos ...

---

### Post by lidex on 2011-04-18
In "Sound Preferences", on the hardware tab, select your analog soundcard and choose 'analog stereo output' or 'analog stereo duplex'
Go into alsamixer:
```
alsamixer
```
Press F6 and select the hdmi soundcard. Mute the outputs using the m key. 
Now switch to the other card and press F3 for playback elements. 
Make sure your levels are up and unmuted.

---

### Post by jchiso on 2011-04-18
That's how things had been pretty much set already, except for muting the HDMI.  It's still the same.  Neither alsamixer nor sound preferences has ever shown a "headphone" or "jacksense" property.

---

### Post by lidex on 2011-04-19
Try a later kernel from here:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
If that doesn't work, you'll need to file a bug. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by jchiso on 2011-04-19
> **lidex said:**
> Try a later kernel from here:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
If that doesn't work, you'll need to file a bug. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

Thanks for your help and numerous suggestions, but this stuff seems too experimental and difficult for me.  Acer is a really common notebook brand and these audio chips are pretty prevalent.  Ubuntu should not have this big a problem with muting onboard speakers and enabling headphone out.

---

### Post by Yellow Pasque on 2011-04-19
The high-def audio spec is a loose one and allows manufacturers a lot of freedom to arrange jacks the way they want. Sadly, that's not good for open drivers as a lot need customization/quirks added to the basic HDA spec. I mean, look at this list:
```
  Model name	Description
  ----------    -----------
ALC880
======
  3stack	3-jack in back and a headphone out
  3stack-digout	3-jack in back, a HP out and a SPDIF out
  5stack	5-jack in back, 2-jack in front
  5stack-digout	5-jack in back, 2-jack in front, a SPDIF out
  6stack	6-jack in back, 2-jack in front
  6stack-digout	6-jack with a SPDIF out
  w810		3-jack
  z71v		3-jack (HP shared SPDIF)
  asus		3-jack (ASUS Mobo)
  asus-w1v	ASUS W1V
  asus-dig	ASUS with SPDIF out
  asus-dig2	ASUS with SPDIF out (using GPIO2)
  uniwill	3-jack
  fujitsu	Fujitsu Laptops (Pi1536)
  F1734		2-jack
  lg		LG laptop (m1 express dual)
  lg-lw		LG LW20/LW25 laptop
  tcl		TCL S700
  clevo		Clevo laptops (m520G, m665n)
  medion	Medion Rim 2150
  test		for testing/debugging purpose, almost all controls can be
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)

ALC260
======
  hp		HP machines
  hp-3013	HP machines (3013-variant)
  hp-dc7600	HP DC7600
  fujitsu	Fujitsu S7020
  acer		Acer TravelMate
  will		Will laptops (PB V7900)
  replacer	Replacer 672V
  favorit100	Maxdata Favorit 100XS
  basic		fixed pin assignment (old default model)
  test		for testing/debugging purpose, almost all controls can
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)

ALC262
======
  fujitsu	Fujitsu Laptop
  hp-bpc	HP xw4400/6400/8400/9400 laptops
  hp-bpc-d7000	HP BPC D7000
  hp-tc-t5735	HP Thin Client T5735
  hp-rp5700	HP RP5700
  benq		Benq ED8
  benq-t31	Benq T31
  hippo		Hippo (ATI) with jack detection, Sony UX-90s
  hippo_1	Hippo (Benq) with jack detection
  sony-assamd	Sony ASSAMD
  toshiba-s06	Toshiba S06
  toshiba-rx1	Toshiba RX1
  tyan		Tyan Thunder n6650W (S2915-E)
  ultra		Samsung Q1 Ultra Vista model
  lenovo-3000	Lenovo 3000 y410
  nec		NEC Versa S9100
  basic		fixed pin assignment w/o SPDIF
  auto		auto-config reading BIOS (default)

ALC267/268
==========
  quanta-il1	Quanta IL1 mini-notebook
  3stack	3-stack model
  toshiba	Toshiba A205
  acer		Acer laptops
  acer-dmic	Acer laptops with digital-mic
  acer-aspire	Acer Aspire One
  dell		Dell OEM laptops (Vostro 1200)
  zepto		Zepto laptops
  test		for testing/debugging purpose, almost all controls can
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)

ALC269
======
  basic		Basic preset
  quanta	Quanta FL1
  laptop-amic	Laptops with analog-mic input
  laptop-dmic	Laptops with digital-mic input
  fujitsu	FSC Amilo
  lifebook	Fujitsu Lifebook S6420
  auto		auto-config reading BIOS (default)

ALC662/663/272
==============
  3stack-dig	3-stack (2-channel) with SPDIF
  3stack-6ch	 3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig	 6-stack with SPDIF
  lenovo-101e	 Lenovo laptop
  eeepc-p701	ASUS Eeepc P701
  eeepc-ep20	ASUS Eeepc EP20
  ecs		ECS/Foxconn mobo
  m51va		ASUS M51VA
  g71v		ASUS G71V
  h13		ASUS H13
  g50v		ASUS G50V
  asus-mode1	ASUS
  asus-mode2	ASUS
  asus-mode3	ASUS
  asus-mode4	ASUS
  asus-mode5	ASUS
  asus-mode6	ASUS
  asus-mode7	ASUS
  asus-mode8	ASUS
  dell		Dell with ALC272
  dell-zm1	Dell ZM1 with ALC272
  samsung-nc10	Samsung NC10 mini notebook
  auto		auto-config reading BIOS (default)

ALC680
======
  base		Base model (ASUS NX90)
  auto		auto-config reading BIOS (default)

ALC882/883/885/888/889
======================
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  macmini3	Macmini 3,1
  mba21		Macbook Air 2,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  imac91	iMac 9,1
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion	Medion Laptops
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m540r	Clevo M540R (6ch + digital)
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)

ALC861/660
==========
  3stack	3-jack
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack with SPDIF I/O
  3stack-660	3-jack (for ALC660)
  uniwill-m31	Uniwill M31 laptop
  toshiba	Toshiba laptop support
  asus		Asus laptop support
  asus-laptop	ASUS F2/F3 laptops
  auto		auto-config reading BIOS (default)

ALC861VD/660VD
==============
  3stack	3-jack
  3stack-dig	3-jack with SPDIF OUT
  6stack-dig	6-jack with SPDIF OUT
  3stack-660	3-jack (for ALC660VD)
  3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
  lenovo	Lenovo 3000 C200
  dallas	Dallas laptops
  hp		HP TX1000
  asus-v1s	ASUS V1Sn
  auto		auto-config reading BIOS (default)

CMI9880
=======
  minimal	3-jack in back
  min_fp	3-jack in back, 2-jack in front
  full		6-jack in back, 2-jack in front
  full_dig	6-jack in back, 2-jack in front, SPDIF I/O
  allout	5-jack in back, 2-jack in front, SPDIF out
  auto		auto-config reading BIOS (default)

AD1882 / AD1882A
================
  3stack	3-stack mode (default)
  6stack	6-stack mode

AD1884A / AD1883 / AD1984A / AD1984B
====================================
  desktop	3-stack desktop (default)
  laptop	laptop with HP jack sensing
  mobile	mobile devices with HP jack sensing
  thinkpad	Lenovo Thinkpad X300
  touchsmart	HP Touchsmart

AD1884
======
  N/A

AD1981
======
  basic		3-jack (default)
  hp		HP nx6320
  thinkpad	Lenovo Thinkpad T60/X60/Z60
  toshiba	Toshiba U205

AD1983
======
  N/A

AD1984
======
  basic		default configuration
  thinkpad	Lenovo Thinkpad T61/X61
  dell_desktop	Dell T3400

AD1986A
=======
  6stack	6-jack, separate surrounds (default)
  3stack	3-stack, shared surrounds
  laptop	2-channel only (FSC V2060, Samsung M50)
  laptop-eapd	2-channel with EAPD (ASUS A6J)
  laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
  ultra		2-channel with EAPD (Samsung Ultra tablet PC)
  samsung	2-channel with EAPD (Samsung R65)
  samsung-p50	2-channel with HP-automute (Samsung P50)

AD1988/AD1988B/AD1989A/AD1989B
==============================
  6stack	6-jack
  6stack-dig	ditto with SPDIF
  3stack	3-jack
  3stack-dig	ditto with SPDIF
  laptop	3-jack with hp-jack automute
  laptop-dig	ditto with SPDIF
  auto		auto-config reading BIOS (default)

Conexant 5045
=============
  laptop-hpsense    Laptop with HP sense (old model laptop)
  laptop-micsense   Laptop with Mic sense (old model fujitsu)
  laptop-hpmicsense Laptop with HP and Mic senses
  benq		Benq R55E
  laptop-hp530	HP 530 laptop
  test		for testing/debugging purpose, almost all controls
		can be adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y

Conexant 5047
=============
  laptop	Basic Laptop config 
  laptop-hp	Laptop config for some HP models (subdevice 30A5)
  laptop-eapd	Laptop config with EAPD support
  test		for testing/debugging purpose, almost all controls
		can be adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y

Conexant 5051
=============
  laptop	Basic Laptop config (default)
  hp		HP Spartan laptop
  hp-dv6736	HP dv6736
  hp-f700	HP Compaq Presario F700
  ideapad	Lenovo IdeaPad laptop
  lenovo-x200	Lenovo X200 laptop
  toshiba	Toshiba Satellite M300

Conexant 5066
=============
  laptop	Basic Laptop config (default)
  hp-laptop	HP laptops, e g G60
  asus		Asus K52JU, Lenovo G560
  dell-laptop	Dell laptops
  dell-vostro	Dell Vostro
  olpc-xo-1_5	OLPC XO 1.5
  ideapad       Lenovo IdeaPad U150
  thinkpad	Lenovo Thinkpad

STAC9200
========
  ref		Reference board
  oqo		OQO Model 2
  dell-d21	Dell (unknown)
  dell-d22	Dell (unknown)
  dell-d23	Dell (unknown)
  dell-m21	Dell Inspiron 630m, Dell Inspiron 640m
  dell-m22	Dell Latitude D620, Dell Latitude D820
  dell-m23	Dell XPS M1710, Dell Precision M90
  dell-m24	Dell Latitude 120L
  dell-m25	Dell Inspiron E1505n
  dell-m26	Dell Inspiron 1501
  dell-m27	Dell Inspiron E1705/9400
  gateway-m4	Gateway laptops with EAPD control
  gateway-m4-2	Gateway laptops with EAPD control
  panasonic	Panasonic CF-74
  auto		BIOS setup (default)

STAC9205/9254
=============
  ref		Reference board
  dell-m42	Dell (unknown)
  dell-m43	Dell Precision
  dell-m44	Dell Inspiron
  eapd		Keep EAPD on (e.g. Gateway T1616)
  auto		BIOS setup (default)

STAC9220/9221
=============
  ref		Reference board
  3stack	D945 3stack
  5stack	D945 5stack + SPDIF
  intel-mac-v1	Intel Mac Type 1
  intel-mac-v2	Intel Mac Type 2
  intel-mac-v3	Intel Mac Type 3
  intel-mac-v4	Intel Mac Type 4
  intel-mac-v5	Intel Mac Type 5
  intel-mac-auto Intel Mac (detect type according to subsystem id)
  macmini	Intel Mac Mini (equivalent with type 3)
  macbook	Intel Mac Book (eq. type 5)
  macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
  macbook-pro	Intel Mac Book Pro 2nd generation (eq. type 3)
  imac-intel	Intel iMac (eq. type 2)
  imac-intel-20	Intel iMac (newer version) (eq. type 3)
  ecs202	ECS/PC chips
  dell-d81	Dell (unknown)
  dell-d82	Dell (unknown)
  dell-m81	Dell (unknown)
  dell-m82	Dell XPS M1210
  auto		BIOS setup (default)

STAC9202/9250/9251
==================
  ref		Reference board, base config
  m1		Some Gateway MX series laptops (NX560XL)
  m1-2		Some Gateway MX series laptops (MX6453)
  m2		Some Gateway MX series laptops (M255)
  m2-2		Some Gateway MX series laptops
  m3		Some Gateway MX series laptops
  m5		Some Gateway MX series laptops (MP6954)
  m6		Some Gateway NX series laptops
  auto		BIOS setup (default)

STAC9227/9228/9229/927x
=======================
  ref		Reference board
  ref-no-jd	Reference board without HP/Mic jack detection
  3stack	D965 3stack
  5stack	D965 5stack + SPDIF
  5stack-no-fp	D965 5stack without front panel
  dell-3stack	Dell Dimension E520
  dell-bios	Fixes with Dell BIOS setup
  volknob	Fixes with volume-knob widget 0x24
  auto		BIOS setup (default)

STAC92HD71B*
============
  ref		Reference board
  dell-m4-1	Dell desktops
  dell-m4-2	Dell desktops
  dell-m4-3	Dell desktops
  hp-m4		HP mini 1000
  hp-dv5	HP dv series
  hp-hdx	HP HDX series
  hp-dv4-1222nr	HP dv4-1222nr (with LED support)
  auto		BIOS setup (default)

STAC92HD73*
===========
  ref		Reference board
  no-jd		BIOS setup but without jack-detection
  intel		Intel DG45* mobos
  dell-m6-amic	Dell desktops/laptops with analog mics
  dell-m6-dmic	Dell desktops/laptops with digital mics
  dell-m6	Dell desktops/laptops with both type of mics
  dell-eq	Dell desktops/laptops
  alienware	Alienware M17x
  auto		BIOS setup (default)

STAC92HD83*
===========
  ref		Reference board
  mic-ref	Reference board with power management for ports
  dell-s14	Dell laptop
  hp		HP laptops with (inverted) mute-LED
  hp-dv7-4000	HP dv-7 4000
  auto		BIOS setup (default)

STAC9872
========
  vaio		VAIO laptop without SPDIF
  auto		BIOS setup (default)

Cirrus Logic CS4206/4207
========================
  mbp55		MacBook Pro 5,5
  imac27	IMac 27 Inch
  auto		BIOS setup (default)

VIA VT17xx/VT18xx/VT20xx
========================
  auto		BIOS setup (default)
```

---

### Post by Yellow Pasque on 2011-04-19
> **jchiso said:**
>  Acer is a really common notebook brand and these audio chips are pretty prevalent.  Ubuntu should not have this big a problem with muting onboard speakers and enabling headphone out.x

Your hardware is very experimental/new, so if it doesn't work, you need to be involved in the process of fixing it, by reporting the problem and providing the information devs request. That is how it works in Ubuntu.

---

### Post by jchiso on 2011-04-23
> **lidex said:**
> ... Reference the Ubuntu-Bug Audio link in my sig.

The link rejected my attempt at a submission.

> **Temüjin said:**
> ... Your hardware is very experimental/new, so if it doesn't work, you need to be involved in the process of fixing it ...

This hardware is not that new.  This notebook was on its way to closeout when I purchased it.  I'm all for helping out, but I think these types of problems have become more prevalent recently as Ubuntu speeds out new releases every six months even as prior releases are only sporadically supported.  One should not have to have five plus years of Ubuntu experience and / or have 1,000 posts on forums like these to use a distribution like this.  If that is the case, then Ubuntu has taken a most unfortunate turn ...

---

### Post by Yellow Pasque on 2011-04-23
I think you'll have more luck getting your issue fixed by taking it directly upstream (to the alsa-dev mailing list).

---

### Post by Yahoé on 2011-04-28
I have the same problem on an Acer 5253 under Ubuntu natty beta2

---

### Post by jchiso on 2011-04-28
That's the model originally discussed here, and others have experienced the same.  No fixes or workarounds yet ...

---

### Post by sidaphextwin on 2011-05-02
Hi, I have had the same problem with acer aspire 5253. Headphones did not work but if the speakers. I found the solution. You have to edit the file **/etc/modprobe.d/alsa-base.conf** and add the following lines:


[B]options snd slots = snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel probe_mask = 1
options snd-hda-intel model = acer position_fix = 1[/B]

By that I sounded like the speakers to my headphones while the solution was to go to alsamixer and Q keys, E, Z and C down the left channel to 0 to MASTER.

I can also control the sound comes through the speakers or headphones.

I hope you like.

Greetings

---

### Post by jchiso on 2011-05-03
> **sidaphextwin said:**
> Hi, I have had the same problem with acer aspire 5253... I found the solution...

Did not work for me.  The hardware device disappears altogether ...

---

### Post by sidaphextwin on 2011-05-03
Sorry, not a permanent solution. Not that with this configuration I could see that the headphones worked, a day after I turned on the laptop and stopped working. In archlinux same thing happened to me, say to the configuration in which the headphones were working and to restart I lost sound again. Do not know what might be happening ...

 If anyone knows anything to say it, please!

---

### Post by samizdatstudio on 2011-05-04
my fujitsu u810 have the same problem,
when i wanna listen music from headphone,speaker and headphone function at same time,it havent change each other,
i no install any additional driver for sound card
is it need install alsa?
where i go change this or fix it?
thanks

if any one know,please help

---

### Post by sidaphextwin on 2011-05-04
Hi, our problem is that the speakers work but headphones do not. To solve your problem just run alsamixer and use the channel keys MASTER Q, E, Z and C to lower the audio left channel. In this way you only have sound in the headphones, if you down the right channel will only have sound from the speakers.

 Greetings

---

### Post by lidex on 2011-05-04
> **samizdatstudio said:**
> my fujitsu u810 have the same problem,
when i wanna listen music from headphone,speaker and headphone function at same time,it havent change each other,
i no install any additional driver for sound card
is it need install alsa?
where i go change this or fix it?
thanks

if any one know,please help

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by sidaphextwin on 2011-05-10
Hello again,
 I managed to run my headphones finally after weeks and weeks of searching in an **acer aspire 5253** .

 Edit the file **/etc/modprobe.d/sound.conf** or create it if not in that directory.

 Insert the following configuration:

 [B]options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=auto

Reboot[/B] 

 Good luck.

---

### Post by jchiso on 2011-05-11
> **sidaphextwin said:**
> ... Edit the file **/etc/modprobe.d/sound.conf** or create it if not in that directory.

 Insert the following configuration:

 [B]options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=auto...

This enables the headphone but does not disable the speakers.  The jacksense does not work ...

---

### Post by monkeyMonk on 2011-06-24
Hi,
  I have an Acer Aspire 5253-BZ602, which runs Ubuntu 11.04 64bit, has been suffered the same problem for a while. 
  Finally, I got the problem fixed, by a long search and trial.  Here is the fix:

  [COLOR=#000000][FONT=Times New Roman][FONT=Verdana]Open the file** /etc/modprobe.d/alsa-base.conf  **(yes, you need sudo)

  Insert the following by the end:
[B]  options  snd-hda-intel model=[COLOR=Red],asus[/COLOR]

  [/B]Save, reboot.  To be aware there is a[COLOR=Black] '[/COLOR][COLOR=Red][COLOR=Black][COLOR=Red],[/COLOR]'[/COLOR] [COLOR=Black]between [COLOR=Yellow][COLOR=Red]**=**[/COLOR] [/COLOR]and [COLOR=Red]**asus**[/COLOR].[/COLOR][/COLOR]

  Bring up  "Sound Preferences", either from panel or System->Preferences->Sound,
  In *Hardware* tab, for the Internal Audio Analog Stereo Duplex, chose profile [/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=Verdana]**Analog Stereo Duplex**. 
  In* Input* tab, chose device for sound input to** Internal Audio Analog Stereo**, and set proper input volume for the Micphone.
  In *Output* tab, chose device for sound output to **Internal Audio Analog Stereo**. 
  Set proper overall Output volume, be sure unckecked Mute.

  Then you should be all right.  This is only for Aspire 5253-BZ602, I will provide a bit more explanation on why this works, if someone shows interests. 
  
[/FONT][/FONT][/COLOR]

---

### Post by lidex on 2011-06-24
> **monkeyMonk said:**
>  I will provide a bit more explanation on why this works, if someone shows interests.   

Please do. I am very interested.

---

### Post by monkeyMonk on 2011-06-24
> **lidex said:**
> Please do. I am very interested.
Ok, I hate typing too much. I will try to be briefly.

In Acer Aspire 5253-BZ602, there are two sound devices available. Check this out by:
[INDENT]**cat /proc/asound/card0/codec* |grep Codec**[/INDENT]
[INDENT]*Codec: ATI R6xx HDMI*[/INDENT]
[INDENT]**cat /proc/asound/card1/codec* |grep Codec**[/INDENT]
[INDENT]*Codec: Conexant CX20584*[/INDENT]

What it tells us is, the sound card0 is the HDMI, and the card1 is the internal speaker and earphone jack. 
Check ALSA official support list, there is no CX20584. By searching on the Internet, I find out it is compatible to Conexant 5066, and fortunately it is on the ALSA list! This gives me the hope that I can tweak/etc/modprobe.d/alsa-base.conf to make it works. Under Conexant 5066, there are models name **thinkpad**, ... and **asus**. I tried each of them, no lucky. Then I remember the "[COLOR="Red"],[/COLOR]" after the "[COLOR="red"]=[/COLOR]", which makes the configuration to the card1 instead of card0. Bingo, then I have all things functional as they should be. All of them, the internal speaker, internal Mic, earphone jack, Mic jack.  
  Hope everyone get rid of the annoying problem. It has been drive me crazy.

Good luck.

---

### Post by lidex on 2011-06-24
Thanks for that. I'd really like to see the configuration changes that creates. Would you be inclined to run the alsa-info script please?
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

---

### Post by monkeyMonk on 2011-06-24
> **lidex said:**
> Thanks for that. I'd really like to see the configuration changes that creates. Would you be inclined to run the alsa-info script please?
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

Hi,
  The info uploaded can be found at [http://www.alsa-project.org/db/?f=60a9a7f275fb9dda526f27a01576d2b52f4db4ec]("http://www.alsa-project.org/db/?f=60a9a7f275fb9dda526f27a01576d2b52f4db4ec")
  I have a customized kernel, but nothing to do with alsa.

Take care,

---

### Post by lidex on 2011-06-25
> **monkeyMonk said:**
> Hi,
  The info uploaded can be found at [http://www.alsa-project.org/db/?f=60a9a7f275fb9dda526f27a01576d2b52f4db4ec]("http://www.alsa-project.org/db/?f=60a9a7f275fb9dda526f27a01576d2b52f4db4ec")
  I have a customized kernel, but nothing to do with alsa.

Take care,

I have no idea how that works. Alsa still sees your hdmi as card 0. You sure it wasn't just selecting the correct (analog) profile that did it?

---

### Post by monkeyMonk on 2011-06-25
> **lidex said:**
> I have no idea how that works. Alsa still sees your hdmi as card 0. You sure it wasn't just selecting the correct (analog) profile that did it?

I'm sure this change works on my Aspire 5253-BZ602. However, I want to clarify, this change does not try to make the internal analog stereo to be the sound card0, instead it does try to configure the card1, the internal analog stereo to have compatible controlling as to Conexant 5066. As result, the internal speaker/Mic works , the external headphone/Mic detection works.

BTW, I don't expect the HDMI sound will work properly by this configuration. Since it wasn't told ALSA how to handle ATI R6xx HDMI on card0. If HDMI just works on this configuration, I will be surprised and feel lucky.

---

### Post by Yellow Pasque on 2011-06-25
Using open-source drivers, HDMI audio will work for RadeonHD 4k cards, but nothing later at this time. fglrx/Catalyst supports HDMI audio, but I'm not sure what cards it supports that on.

---

### Post by jchiso on 2011-06-25
> **monkeyMonk said:**
> ... Finally, I got the problem fixed, by a long search and trial.  Here is the fix:

Open the file** /etc/modprobe.d/alsa-base.conf  **(yes, you need sudo)

  Insert the following by the end:
[B]  options  snd-hda-intel model=[COLOR=Red],asus[/COLOR]
... 

Thanks.  This actually works!  For the record, I'm running 32-bit Maverick ...

---

### Post by monkeyMonk on 2011-06-25
> **jchiso said:**
> Thanks.  This actually works!  For the record, I'm running 32-bit Maverick ...

Congratulation. Just realized you bring up this thread. 
Do you mind to tag the thread's title to be resolved?

Take care.

---

### Post by jchiso on 2011-06-26
> **monkeyMonk said:**
> ... Do you mind to tag the thread's title to be resolved? ...

Not at all.  Now if only I could correct the spelling of "disabled" ...

---

### Post by jchiso on 2011-06-27
> **jchiso said:**
> Not at all.  Now if only I could correct the spelling of "disabled" ...

Well, it's back to being "unsolved".  The recent system updates undid the fix ...

---

### Post by lidex on 2011-06-28
> **jchiso said:**
> Well, it's back to being "unsolved".  The recent system updates undid the fix ...

Did you update alsa with the script? If so, you need to re-run it with the -i option when a new kernel is installed. See the link in my sig.

---

### Post by jchiso on 2011-06-28
> **lidex said:**
> Did you update alsa with the script? If so, you need to re-run it with the -i option when a new kernel is installed. See the link in my sig.

Well, I did that and now the sound card (hardware device) is completely gone from the Sound Preferences panel ...

---

### Post by jchiso on 2011-06-28
> **lidex said:**
> Did you update alsa with the script? If so, you need to re-run it with the -i option when a new kernel is installed. See the link in my sig.

> **jchiso said:**
> Well, I did that and now the sound card (hardware device) is completely gone from the Sound Preferences panel ...

I had to run the script with each of the -c -d and -i options to get the sound device to return.  Local audio works, but I couldn't hear any streamed online audio.  I checked the alsa.conf file and had to re-add the pulseaudio line to get it to work ...

---

### Post by ApocryphalAuthor on 2011-08-03
> **monkeyMonk said:**
> Hi,
  I have an Acer Aspire 5253-BZ602, which runs Ubuntu 11.04 64bit, has been suffered the same problem for a while. 
  Finally, I got the problem fixed, by a long search and trial.  Here is the fix:

  [COLOR=#000000][FONT=Times New Roman][FONT=Verdana]Open the file** /etc/modprobe.d/alsa-base.conf  **(yes, you need sudo)

  Insert the following by the end:
[B]  options  snd-hda-intel model=[COLOR=Red],asus[/COLOR]

  [/B]Save, reboot.  To be aware there is a[COLOR=Black] '[/COLOR][COLOR=Red][COLOR=Black][COLOR=Red],[/COLOR]'[/COLOR] [COLOR=Black]between [COLOR=Yellow][COLOR=Red]**=**[/COLOR] [/COLOR]and [COLOR=Red]**asus**[/COLOR].[/COLOR][/COLOR]

  Bring up  "Sound Preferences", either from panel or System->Preferences->Sound,
  In *Hardware* tab, for the Internal Audio Analog Stereo Duplex, chose profile [/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=Verdana]**Analog Stereo Duplex**. 
  In* Input* tab, chose device for sound input to** //Internal Audio Analog Stereo**, and set proper input volume for the Micphone.
  In *Output* tab, chose device for sound output to **Internal Audio Analog Stereo**. 
  Set proper overall Output volume, be sure unckecked Mute.

  Then you should be all right.  This is only for Aspire 5253-BZ602, I will provide a bit more explanation on why this works, if someone shows interests. 
  
[/FONT][/FONT][/COLOR]

This solution worked perfectly for my Asus Aspire 5253-BZ893.  I'm running Lubuntu 11.04 64 Bit.  Thanks a lot man!  I owe you a beer. :)

---

### Post by kpike on 2011-08-24
The initial fix worked for me. I'm running 64 bit Ubuntu 11.04 on a Fujitsu T731.

---

### Post by mercvrivs on 2011-11-08
> **lidex said:**
> I would remove that acer model switch from alsa-base.conf then update your alsa-modules and rerun the info script.

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

This solved my problem as well... Thank you very much!!:)

I'm running Ubuntu 10.10 Maverick Meerkat 32 bits

---

