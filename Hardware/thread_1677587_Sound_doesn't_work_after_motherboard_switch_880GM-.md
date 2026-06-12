---
title: "Sound doesn't work after motherboard switch: 880GM-D2H"
date: 2011-01-28
forum: Hardware
---

### Post by texaswriter on 2011-01-28
Switched out my motherboard, cpu, and memory and now my sound doesn't work. 

Everything else seems to work fine. Is there anything that I can do to update anything? 

Here is some information recommended by the ubuntu audio troubleshooting page


```

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat Jan 29 04:40:50 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      GA-880GM-D2H
Product Version:    


!!Kernel Information
!!------------------

Kernel release:    2.6.32-28-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


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

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdffc000 irq 19


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383
	Subsystem: 1458:a002
--
01:00.1 0403: 1002:aa30
	Subsystem: 1682:aa30


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	single_cmd : N

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC887
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0887
Subsystem Id: 0x1458a002
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014410: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19c40: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c50: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181344f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x4, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x593301f0: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005c603: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = UNKNOWN
    DefAssociation = 0x0, Sequence = 0x3
  Pin-ctls: 0x20: IN
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x014b6130: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x01cb7160: [Jack] SPDIF In at Ext Rear
    Conn = Comb, Color = Yellow
    DefAssociation = 0x6, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=24
  Processing Coefficient: 0xc00
  Coefficient Index: 0x0c
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x25 0x0b
Codec: ATI R6xx HDMI
Address: 0
Function Id: 0x1
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
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
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 10 Jan 29  2011 /dev/snd/controlC0
crw-rw----  1 root audio 116, 13 Jan 29  2011 /dev/snd/controlC1
crw-rw----  1 root audio 116,  9 Jan 29  2011 /dev/snd/hwC0D0
crw-rw----  1 root audio 116, 12 Jan 29  2011 /dev/snd/hwC1D0
crw-rw----  1 root audio 116,  8 Jan 28 22:29 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  7 Jan 28 22:28 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  6 Jan 28 22:18 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116,  5 Jan 28 22:18 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  4 Jan 29  2011 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116, 11 Jan 28 22:21 /dev/snd/pcmC1D3p
crw-rw----  1 root audio 116,  3 Jan 29  2011 /dev/snd/seq
crw-rw----  1 root audio 116,  2 Jan 29  2011 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Jan 29  2011 .
drwxr-xr-x 3 root root 300 Jan 29  2011 ..
lrwxrwxrwx 1 root root  12 Jan 29  2011 pci-0000:00:14.2 -> ../controlC0
lrwxrwxrwx 1 root root  12 Jan 29  2011 pci-0000:01:00.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

amixer: Mixer load hw:0 error: Invalid argument
Card hw:0 'SB'/'HDA ATI SB at 0xfe024000 irq 16'
  Mixer name	: 'Realtek ALC887'
  Components	: 'HDA:10ec0887,1458a002,00100302'
  Controls      : 40
amixer: Mixer hw:0 load error: Invalid argument

!!-------Mixer controls for card 1 [HDMI]

Card hw:1 'HDMI'/'HDA ATI HDMI at 0xfdffc000 irq 19'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100100'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
hidp
rfcomm
sco
bridge
binfmt_misc
stp
bnep
l2cap
ppdev
vboxnetadp
vboxnetflt
vboxdrv
snd_hda_codec_atihdmi
snd_hda_codec_realtek
btusb
snd_pcm_oss
snd_hda_intel
bluetooth
snd_mixer_oss
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
fbcon
tileblit
font
bitblit
snd
softcursor
edac_core
edac_mce_amd
soundcore
snd_page_alloc
fglrx
vga16fb
vgastate
i2c_piix4
lp
parport
usbhid
hid
floppy
ahci
pata_atiixp
r8169
mii


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x411111f0
0x12 0x411111f0
0x14 0x01014410
0x15 0x411111f0
0x16 0x411111f0
0x17 0x411111f0
0x18 0x01a19c40
0x19 0x02a19c50
0x1a 0x0181344f
0x1b 0x02214c20
0x1c 0x593301f0
0x1d 0x4005c603
0x1e 0x014b6130
0x1f 0x01cb7160

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   11.987952] Bluetooth: HCI socket layer initialized
[   11.992858] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.009209] Bluetooth: Generic Bluetooth USB driver ver 0.6
--
[   12.053468] Console: switching to colour frame buffer device 80x30
[   12.185598] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input9
[   12.192547] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.192614] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.192962] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   12.192996] HDA Intel 0000:01:00.1: setting latency timer to 64
[   12.297872] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.301451] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.305304] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.308492] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.311820] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.315008] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.318220] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.321465] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.324786] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.327998] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.331170] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.334358] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.337646] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.340967] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.344174] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.347375] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.350596] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.353777] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.356943] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.360127] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.363276] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.366443] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.369588] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.372842] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.376968] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.380282] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.383617] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.386868] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.390236] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.394077] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.397612] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.402324] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.405583] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.408760] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.412061] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.415266] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.418499] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.421769] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.425003] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.428177] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.431913] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.437243] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.441477] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.448471] EXT4-fs (sdc1): mounted filesystem with ordered data mode
--
[   17.170752]   groups: 3 0 1 2
[   17.821479] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   18.460250] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   18.500214] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   23.450043] eth1: no IPv6 routers present
[   31.332580] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   32.490258] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   32.540205] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1353.435851] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1353.447027] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[ 1353.995649] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)




```

---

### Post by texaswriter on 2011-01-30
bumpies:popcorn:

---

### Post by gordintoronto on 2011-01-30
Do both devices show up in Preferences/Sound under Hardware? Which one is selected? Which one do you use? (In other words, do you use HDMI out?) And in the Output tab, you have confirmed that the device is not muted, and is set to fairly high volume?

---

### Post by texaswriter on 2011-01-30
> **gordintoronto said:**
> Do both devices show up in Preferences/Sound under Hardware? Which one is selected? Which one do you use? (In other words, do you use HDMI out?) And in the Output tab, you have confirmed that the device is not muted, and is set to fairly high volume?

Yes, one of the devices is from my ATI graphics card (not built-in). That's if you have HDMI out to a monitor that has a built-in speaker (I would assume). 

The volume are both high and not-muted. The speaker also works.

---

### Post by lidex on 2011-01-30
Try re-installing alsa first. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by texaswriter on 2011-01-30
> **lidex said:**
> Try re-installing alsa first. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```**Reboot.**

Okay did that. Here is the output, in case it is relevant. 

> 
~$ sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
[sudo] password for :
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.32-28-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.32-28-generic"
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-2.6.32-28-generic 
  linux-sound-base 
0 packages upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1,846kB/33.5MB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main alsa-base 1.0.22.1+dfsg-0ubuntu3 [273kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main alsa-utils 1.0.22-0ubuntu5 [1,102kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libasound2 1.0.22-0ubuntu7 [437kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main linux-sound-base 1.0.22.1+dfsg-0ubuntu3 [33.7kB]
Fetched 1,846kB in 9s (191kB/s)                                                 
Preconfiguring packages ...
(Reading database ... 280571 files and directories currently installed.)
Preparing to replace linux-image-2.6.32-28-generic 2.6.32-28.55 (using .../linux-image-2.6.32-28-generic_2.6.32-28.55_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.32-28-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Preparing to replace alsa-base 1.0.22.1+dfsg-0ubuntu3 (using .../alsa-base_1.0.22.1+dfsg-0ubuntu3_all.deb) ...
Unpacking replacement alsa-base ...
Preparing to replace alsa-utils 1.0.22-0ubuntu5 (using .../alsa-utils_1.0.22-0ubuntu5_amd64.deb) ...
Unpacking replacement alsa-utils ...
Preparing to replace libasound2 1.0.22-0ubuntu7 (using .../libasound2_1.0.22-0ubuntu7_amd64.deb) ...
Unpacking replacement libasound2 ...
Preparing to replace linux-sound-base 1.0.22.1+dfsg-0ubuntu3 (using .../linux-sound-base_1.0.22.1+dfsg-0ubuntu3_all.deb) ...
Unpacking replacement linux-sound-base ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up linux-image-2.6.32-28-generic (2.6.32-28.55) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-28-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-28.55 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-28.55 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic

Setting up libasound2 (1.0.22-0ubuntu7) ...

Setting up linux-sound-base (1.0.22.1+dfsg-0ubuntu3) ...

Setting up alsa-base (1.0.22.1+dfsg-0ubuntu3) ...

Setting up alsa-utils (1.0.22-0ubuntu5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Now, if you'll notice, one of the things wasn't found the kernel module whatever... otherwise everything proceeded along nicely. 

Something went wrong when rebooting, but not sure it had anything to do with this. Upon rebooting, Ubuntu had problems mounting disks and gave me the message "... I to ignore, S to skip or M for manual recovery". Pressing I just lent to waiting forever without anything happening. S would let me login but it didn't mount anything and didn't seem to finish loading, therefore just waiting without much happening, M let me scan and even mount all my devices, but when I pressed exit, it went to a blank screen and stayed there forever. . .


I used a LiveCD to boot and use GParted to check all disks. I also used Manual Recovery to successfully mount all devices and navigate them to ensure contents. 

Anyways, after restarting enough times I guess my computer gave up  pestering me for now... I was able to reboot just fine... all things  loaded.

So, hopefully, we should be able to disregard this detour. 

Anyways, my sound is still not working.

I've never seen a bios that has the sound turned off by default, but I will do the idiot check and reboot to check my bios. Let's hope I don't have problems rebooting again.

ALSO, for what it is worth, my sound **did not work **when I booted from the LiveCD (Ubuntu 10.04). I don't know how relevant that is considering the Ubuntu LiveCD is from roughly a week or so after it was released. 

This is my motherboard: Gigabyte 880GM-D2H

*BACK*

So, I rebooted, and checked in the bios. I believe audio is enabled in the audio due to the following: "Onboard Audio Function" : "Enabled"

Anyways, I did have problems rebooting. Got the "I, S, M" message again. This time pressing manual recovery, mounting the relevant disks, and exiting the root terminal had the appropriate effect, that is I was able to log in just fine. 

**Is this a motherboard driver support issue? **Is it possible I need to file a bug report or are there other things we can try still?

---

### Post by lidex on 2011-01-30
This output is problematic:
```
!!-------Mixer controls for card 0 [SB]

amixer: Mixer load hw:0 error: Invalid argument
Card hw:0 'SB'/'HDA ATI SB at 0xfe024000 irq 16'
  Mixer name	: 'Realtek ALC887'
  Components	: 'HDA:10ec0887,1458a002,00100302'
  Controls      : 40
amixer: Mixer hw:0 load error: Invalid argument
```
That from your initial alsa-info.txt. Run it again so we can see where we are. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

Probably good to check bios as well:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by texaswriter on 2011-01-31
> **lidex said:**
> This output is problematic:
```
!!-------Mixer controls for card 0 [SB]

amixer: Mixer load hw:0 error: Invalid argument
Card hw:0 'SB'/'HDA ATI SB at 0xfe024000 irq 16'
  Mixer name    : 'Realtek ALC887'
  Components    : 'HDA:10ec0887,1458a002,00100302'
  Controls      : 40
amixer: Mixer hw:0 load error: Invalid argument
```That from your initial alsa-info.txt. Run it again so we can see where we are. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.


Here's the fresh link: 

[http://www.alsa-project.org/db/?f=5a674bba011902dfaf89cbe01d85b0dd189f3785](http://www.alsa-project.org/db/?f=5a674bba011902dfaf89cbe01d85b0dd189f3785)

> 
Probably good to check bios as well:
```
sudo dmidecode -t bios

``````

# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Award Software International, Inc.
    Version: F6
    Release Date: 08/31/2010
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported

Handle 0x0020, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1


```
> ```

sudo dmidecode -t baseboard

``````

# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: GA-880GM-D2H
    Version: x.x
    Serial Number:  

```

Thanks for the help so far.

---

### Post by lidex on 2011-01-31
Still there. Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by texaswriter on 2011-01-31
> **lidex said:**
> Still there. Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Okay, done. 

> 
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```**Reboot**
Okay, problem here because there isn't a linux-alsa-driver-modules-kernel-generic for my kernel. I am using: 

Here is my current kernel version: 
```
:~$ uname -r
**2.6.32-28-generic**

```Here are the available versions of that: 
```
texaswriter@texaswriter-desktop:~$ sudo apt-get install linux-alsa-driver-modules-2.6.32-***[TAB KEY]***
linux-alsa-driver-modules-2.6.32-17-generic
linux-alsa-driver-modules-2.6.32-17-server
linux-alsa-driver-modules-2.6.32-18-generic
linux-alsa-driver-modules-2.6.32-18-server
linux-alsa-driver-modules-2.6.32-19-generic
linux-alsa-driver-modules-2.6.32-19-server
linux-alsa-driver-modules-2.6.32-20-generic
linux-alsa-driver-modules-2.6.32-20-server
linux-alsa-driver-modules-2.6.32-21-generic
linux-alsa-driver-modules-2.6.32-21-server
linux-alsa-driver-modules-2.6.32-22-generic
linux-alsa-driver-modules-2.6.32-22-server
linux-alsa-driver-modules-2.6.32-23-generic
linux-alsa-driver-modules-2.6.32-23-server
linux-alsa-driver-modules-2.6.32-24-generic
linux-alsa-driver-modules-2.6.32-24-server
linux-alsa-driver-modules-2.6.32-25-generic
linux-alsa-driver-modules-2.6.32-25-server
linux-alsa-driver-modules-2.6.32-26-generic
linux-alsa-driver-modules-2.6.32-26-server
linux-alsa-driver-modules-2.6.32-27-generic
linux-alsa-driver-modules-2.6.32-27-server

```I installed ```
linux-alsa-driver-modules-2.6.32-27-generic
``` and rebooted. 

> 
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.Get back to you on this as soon as I reboot. 

EDIT:```
:~$ sudo alsamixer
cannot load mixer controls: Invalid argument

```same without sudo...

but, if it helps, there is an attached screenshot of which is selected and the volume. 

Also, if I need to, I can boot into a previous kernel. Only problem is that that menu doesn't normally come up when I restart my computer.

---

### Post by texaswriter on 2011-01-31
See above for all the details so far, below is a quick summary

1) Audio appears to be enabled in the bios

2) Properly selected and not-muted in audio mixer

3) No sound either when booting from the liveCD

Anyways, thanks for the help so far. I hope we can get this squared away.

---

### Post by gordintoronto on 2011-01-31
> **texaswriter said:**
> Yes, one of the devices is from my ATI graphics card (not built-in). That's if you have HDMI out to a monitor that has a built-in speaker (I would assume). 

The volume are both high and not-muted. The speaker also works.

Most HDMI displays are high-def TVs. You didn't explicitly say that the other sound device is the one which is selected, but I assume that is the case?

---

### Post by gordintoronto on 2011-01-31
> **texaswriter said:**
> Okay, problem here because there isn't a linux-alsa-driver-modules-kernel-generic for my kernel. I am using: 

Here is my current kernel version: 
```
:~$ uname -r
**2.6.32-28-generic**

```

Also, if I need to, I can boot into a previous kernel. Only problem is that that menu doesn't normally come up when I restart my computer.

If you hold down the shift key, the menu should appear.

If you use Administration/Synaptic, and look at the detail for the alsa-driver-modules... it has important comments.

---

### Post by lidex on 2011-01-31
Yep. You'll need to boot into the kernel matching the alsa-modules version number.

---

### Post by texaswriter on 2011-02-05
Okay, just got around to implementing the last suggestions and sound works great. 

Thanks everybody for all the help.

---

### Post by Harold Zable on 2011-02-05
I've got a Gigabyte D525-TUD motherboard, and was experiencing similar sound problems. Although I suppose it's obvious in retrospect, updating the ALSA drivers as described above fixed my problem, too.

Thanks!

--Harold Z.

---

### Post by texaswriter on 2011-04-22
haha, installed Ubuntu Studio and referred back to this post again!!!

Thanks again for all the help!!

:popcorn::KS:popcorn::KS:popcorn::KS:D:P

---

