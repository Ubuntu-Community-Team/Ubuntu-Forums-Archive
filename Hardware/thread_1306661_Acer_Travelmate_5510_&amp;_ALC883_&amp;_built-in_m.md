---
title: "Acer Travelmate 5510 &amp; ALC883 &amp; built-in mic not recording &amp; ubuntu9.10"
date: 2009-10-30
forum: Hardware
---

### Post by fragu81 on 2009-10-30
Solved because I installed ubuntu 11.04 and the microphone works. I would really appreciate if someone told me WHY??
Oh , and after the upgrade I can't connect to my motorola Milestone wireless hotspot.

[B][COLOR=Red]SOLVED: installed ubuntu 10.04. tether working, microphone not. AND I followed this tutorial:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)[/COLOR][/B]

Great! 10x!



Hello ppl! some help would be much apreciated!

Can't record from mic (the built in one), can't use the mic.
Tried to unmute everything in alsamixer -- things still don't work
tried to put "options snd-hda-intel model=acer" or acer-aspire or 3stack-6ch in /etc/modprobe.d/alsa-base.conf and nothing worked so far.
  
this is what alsa says:

```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Fri Oct 30 18:16:22 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      Acer            
Product Name:      TravelMate 5510 


!!Kernel Information
!!------------------

Kernel release:    2.6.31-14-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

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
                      HDA ATI SB at 0xf0500000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:437b (rev 01)
    Subsystem: 1025:009f
--
    Region 1: Memory at f0401000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
--
    Region 0: Memory at f0401400 (32-bit, non-prefetchable) [size=128]
    Capabilities: [80] Power Management version 2
--
    Region 0: Memory at f0401800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
--
    Region 0: Memory at f0401c00 (32-bit, non-prefetchable) [size=128]
    Capabilities: [80] Power Management version 2
--
    Region 0: Memory at f0401100 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2


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
snd-hda-intel: power_save=10 power_save_controller=N


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : 0
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 10
    power_save_controller : N
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC883
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0883
Subsystem Id: 0x1025009f
Revision Id: 0x100002
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0xc2211110: [Both] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a19930: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x0281313f: [Jack] Line In at Ext Front
    Conn = 1/8, Color = Blue
    DefAssociation = 0x3, Sequence = 0xf
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4015130d: [N/A] Speaker at Ext N/A
    Conn = Optical, Color = Black
    DefAssociation = 0x0, Sequence = 0xd
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x02451120: [Jack] SPDIF Out at Ext Front
    Conn = Optical, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
  Processing Coefficient: 0x00
  Coefficient Index: 0x0c
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b
Codec: Conexant ID 2c06
Address: 1
Function Id: 0x2
Vendor Id: 0x14f12c06
Subsystem Id: 0x1025009f
Revision Id: 0x100000
Modem Function Group: 0x2
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 10 Oct 30 19:56 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  9 Oct 30 19:56 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  8 Oct 30 19:56 /dev/snd/hwC0D1
crw-rw----+ 1 root audio 116,  7 Oct 30 19:57 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  6 Oct 30 19:57 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  5 Oct 30 19:57 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  4 Oct 30 19:56 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  3 Oct 30 19:56 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Oct 30 19:56 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Oct 30 19:56 .
drwxr-xr-x 3 root root 240 Oct 30 19:56 ..
lrwxrwxrwx 1 root root  12 Oct 30 19:56 pci-0000:00:14.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xf0500000 irq 16'
  Mixer name    : 'Realtek ALC883'
  Components    : 'HDA:10ec0883,1025009f,00100002 HDA:14f12c06,1025009f,00100000'
  Controls      : 23
  Simple ctrls  : 13
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [34.50dB] [on]
  Front Right: Capture 31 [100%] [34.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [34.50dB] [on]
  Front Right: Capture 31 [100%] [34.50dB] [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Front Playback Volume'
        value.0 31
        value.1 31
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Front Playback Switch'
        value.0 true
        value.1 true
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value.0 31
        value.1 31
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Mic Playback Switch'
        value.0 true
        value.1 true
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
    }
    control.6 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Line Playback Switch'
        value.0 false
        value.1 false
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3000
        iface MIXER
        name 'Mic Boost'
        value.0 0
        value.1 0
    }
    control.8 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 true
        value.1 true
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1200
        comment.dbmax 3450
        iface MIXER
        name 'Capture Volume'
        value.0 31
        value.1 31
    }
    control.11 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1200
        comment.dbmax 3450
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 31
        value.1 31
    }
    control.12 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 Line
        iface MIXER
        name 'Input Source'
        value Mic
    }
    control.13 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 Line
        iface MIXER
        name 'Input Source'
        index 1
        value Mic
    }
    control.14 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.15 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.16 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.17 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value false
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Beep Playback Volume'
        value.0 0
        value.1 0
    }
    control.20 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Beep Playback Switch'
        value.0 false
        value.1 false
    }
    control.21 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value 31
    }
    control.22 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.23 {
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
binfmt_misc
ppdev
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
vboxnetadp
vboxnetflt
arc4
ecb
ath5k
snd_hwdep
mac80211
ath
snd_pcm_oss
snd_mixer_oss
bridge
stp
vboxdrv
bnep
snd_pcm
btusb
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
joydev
snd_seq_midi_event
pcmcia
snd_seq
uvcvideo
snd_timer
snd_seq_device
cfg80211
lp
parport
videodev
acer_wmi
psmouse
sdhci_pci
sdhci
yenta_socket
v4l1_compat
snd
rsrc_nonstatic
pcmcia_core
soundcore
snd_page_alloc
led_class
serio_raw
k8temp
i2c_piix4
shpchp
iptable_filter
ip_tables
x_tables
usbhid
8139too
8139cp
mii
radeon
ttm
drm
i2c_algo_bit
ati_agp
agpgart
video
output


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x14 0xc2211110
0x15 0x411111f0
0x16 0x411111f0
0x17 0x411111f0
0x18 0x02a19930
0x19 0x411111f0
0x1a 0x0281313f
0x1b 0x411111f0
0x1c 0x411111f0
0x1d 0x4015130d
0x1e 0x02451120
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:
0x73 0x016a10f0

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   14.095683] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   14.304865] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.403937] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   14.404130] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input12
[   14.569381] ADDRCONF(NETDEV_UP): wlan0: link is not ready
--
[   79.416068] Clocksource tsc unstable (delta = -298938438 ns)
[ 1213.864014] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x001f000a
[ 1214.868016] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x001f000a
[ 1214.868096] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000b
[ 1214.868102] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000b
[ 1214.868105] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000b
[ 1214.868108] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868110] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868113] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868115] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868118] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868120] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868123] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868125] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868128] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868130] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868133] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868135] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868138] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868140] hda-intel: spurious response 0x0:0x0, last cmd=0x1f000d
[ 1214.868143] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868146] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868148] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868151] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868153] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868156] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868158] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868161] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868163] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868166] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868168] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868171] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868173] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868176] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868178] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868181] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868183] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0012
[ 1214.868186] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868188] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868191] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868193] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868196] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868199] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868201] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868204] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868206] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868209] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868211] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868214] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868216] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868219] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868221] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868224] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0004
[ 1214.868226] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868229] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868231] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868234] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868236] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868239] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868241] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868244] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868246] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868249] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868251] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868254] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868256] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868259] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868262] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868264] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868267] hda-intel: spurious response 0x0:0x0, last cmd=0x1f0011
[ 1214.868269] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868272] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868274] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868277] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868279] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868282] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868284] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868287] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868289] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868292] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868295] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868297] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868300] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868302] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868305] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1600
[ 1214.868307] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868310] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868312] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868315] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868317] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868320] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868322] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868325] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868328] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868330] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868333] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868335] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868338] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868340] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868343] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868345] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868348] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1700
[ 1214.868350] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868353] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868355] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868358] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868360] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868363] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868365] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868368] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868370] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868373] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868375] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868378] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868380] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868383] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868385] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868388] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868390] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1800
[ 1214.868393] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868396] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868398] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868401] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868403] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868406] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868408] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868411] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868413] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868416] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868418] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868421] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868423] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868426] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868428] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868431] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1900
[ 1214.868433] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868436] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868438] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868441] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868443] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868446] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868449] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868451] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868454] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868456] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868459] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868461] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868464] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868466] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868469] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868471] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1a00
[ 1214.868474] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1500
[ 1214.868476] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1500
[ 1214.868479] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1500
[ 1214.868481] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1500
[ 1214.868484] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1500
[ 1214.868486] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1500
[ 1214.868489] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1500
[ 1214.868491] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1500
[ 1214.868494] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1500
[ 1214.868496] hda-intel: spurious response 0x0:0x0, last cmd=0x1f1500


```Thank you!

---

### Post by fragu81 on 2009-10-31
Ok! I think It has something to do with the modem. I have a foxconn conexant modem in this laptop but ubuntu says nothing of it.
Searched and instaled alsa driver from linuxant and now ubuntu say's something about a HFS modem being detected but no driver (I didn't install the driver). Meanwhile, the apearance of alsamixer changed. I tried to put a "model=acer" in alsa-base.conf (/etc/modprobe.d/) but it's not ok (I mean that it didn't solve the problem).

So for now I think the problem is about ALSA ALC883 and Conexant. 

HELP??? Somebody???

---

### Post by sexyclient on 2009-10-31
I've got the same problem!

I'm on a sony vaio tz that has a "Front Mic" that I just can't get to actually record from.  Oddly enough, I was able to get it working on the KDE version of both OpenSuse and Fedora.  All I did was change the source so that "Front Mic" was the first capture device, and then it worked.

Not so much now, though, it's a shame.  There's this tune I've got in my head that I'm just dying to hum into midomi.com and get the name of...

---

### Post by fragu81 on 2009-10-31
I really don't kow what to do next. with linuxant drivers it didn't work, i compiled from alsa and nothing.

Why does it uses snd-hda-intel and not snd-atiixp-modem and audio? Would it work if it used that?
```

description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:f0500000-f0503fff

```

There is a kubuntu page with the same problem I gues:

[https://wiki.kubuntu.org/SndHdaIntelSoundProblems](https://wiki.kubuntu.org/SndHdaIntelSoundProblems)

```

 cat /proc/asound/card*/codec\#*|grep -i codec
Codec: Realtek ALC883
Codec: Conexant ID 2c06

```

Don't know... should I wait and hope for the best? Is it an alsa problem? Or is there anything else I can do?

---

### Post by sexyclient on 2009-11-01
Got mines working ;D

After setting different values for input 1 (front mic) 2 and 3 in alsamixer, right-click on the volume tray-icon and bringup "sound preferences."  In the "Hardware" tab, I selected the "internal audio" and changed the profile to "analog stereo duplex," (though this was the origonal value that I changed in an attempt to fix the problem.)

Now on the input tab there's the option to select "Microphone 2."  This option wasn't there before I configured alsamixer so that was probably the key.  Hope it works for you.

---

### Post by fragu81 on 2009-11-04
No, that's not it.
Waiting...

---

### Post by LeBurt on 2009-11-11
I have a different motherboard but the same ALC833 codec. I have never been able to get the microphone to work, no matter what I tried. I still look around once in a while to see if a solution has been found. Apparently not...

---

### Post by fragu81 on 2009-12-08
Yes. Still nothing.

---

