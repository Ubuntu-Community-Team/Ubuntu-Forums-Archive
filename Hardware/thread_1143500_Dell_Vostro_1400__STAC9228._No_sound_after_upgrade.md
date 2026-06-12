---
title: "Dell Vostro 1400 / STAC9228. No sound after upgrade to 9.04"
date: 2009-04-30
forum: Hardware
---

### Post by peripatetic on 2009-04-30
OK, so I've spent about a day on this so far trying various things from around the forums. 

I've tried the PulseAudio guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I've tried re-installing pulseaudio and alsa. 

I've tried everything in this guide [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

I've tried every combination of settings in Sound Manager and Volume control (autodetect, pulseaudion, alsa, oss etc).

I've tried adding many different options to /etc/modprobe.d/alsa-base.conf and rebooting. 

Sound worked fine in both 8.04 and 8.10. It worked fine when I booted off the 9.04 live CD to test it. However after running the dist-upgrade from 8.10 to 9.04 I have no sound. After installing the Pulseaudio volume control I can see applications are playing sound OK and communicating with pulseaudio. However no sound comes out of the speakers or headphone sockets. 

Here are some diagnostics

```
aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

```

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 0227
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

```
lsmod | grep snd
snd_hda_intel         435636  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

```

The output of alsa-info.sh is here: [http://www.alsa-project.org/db/?f=46b32123ee285a386e6f3469d6649384e5d4a056](http://www.alsa-project.org/db/?f=46b32123ee285a386e6f3469d6649384e5d4a056)

I'm really at a loss now. Especially strange is the fact that I can boot from the CD and audio works. I've checked the alsa-base.conf and its identical when booting from the CD. One strange thing I've noticed is that when I boot from the CD I get an extra channel in the Volume control, Headphones, which is not present when I boot from the hard disk. 

Any ideas here?

---

### Post by peripatetic on 2009-04-30
I forgot to add. This has actually happened on both my laptops. Completely different manufacturers, models, different soundchips. But I want to get one fixed first before I mention the other one. 

Here is the output of alsa-info.sh when running from the Live CD. In case it means something to someone, and you can compare it to the other version above. 
 
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.56
!!################################

!!Script ran on: Thu Apr 30 03:32:51 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!Kernel Information
!!------------------

Kernel release:    2.6.28-11-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.18rc3
Library version:    1.0.18
Utilities version:  1.0.18


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

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:284b (rev 02)
	Subsystem: 1028:0227


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
bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
enable_msi : 0
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
power_save : 0
power_save_controller : Y
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: SigmaTel STAC9228
Address: 0
Vendor Id: 0x83847616
Subsystem Id: 0x10280227
Revision Id: 0x100201
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x0e, stepsize=0x05, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=3, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[2]: enable=1, dir=1, wake=0, sticky=0, data=1
Node 0x02 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x5d 0x5d]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x03 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x76 0x76]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x04 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x54 0x54]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x05 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x76 0x76]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x06 [Vendor Defined Widget] wcaps 0xfd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: setting=D3, actual=D3
  Delay: 13 samples
Node 0x07 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x1b
  Processing caps: benign=0, ncoeff=0
Node 0x08 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x1c
  Processing caps: benign=0, ncoeff=0
Node 0x09 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x1d
  Processing caps: benign=0, ncoeff=0
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000173f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=30, enabled=1
  Connection: 2
     0x02* 0x03
Node 0x0b [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000173f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x02 0x03*
Node 0x0c [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x90a79130: [Fixed] Mic at Int N/A
    Conn = Analog, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=30, enabled=1
  Connection: 1
     0x03
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000173f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x0e [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a79130: [Jack] Mic at Ext Front
    Conn = Analog, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x0227011f: [Jack] HP Out at Ext Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0xf
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=30, enabled=1
  Connection: 1
     0x05
Node 0x10 [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
  Pin Default 0x40f000f2: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x2
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x11 [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
  Pin Default 0x40f000f3: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x3
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x03
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x40f000f4: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x4
  Pin-ctls: 0x00:
Node 0x13 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x90a60040: [Fixed] Mic at Int N/A
    Conn = Digital, Color = Unknown
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x20: IN
Node 0x14 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x40f000f5: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x5
  Pin-ctls: 0x20: IN
Node 0x15 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x03 0x03]
  Connection: 9
     0x0e 0x12 0x0f 0x0b 0x0c* 0x0d 0x0a 0x10 0x11
Node 0x16 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x03 0x03]
  Connection: 9
     0x0e 0x12 0x0f 0x0b 0x0c* 0x0d 0x0a 0x10 0x11
Node 0x17 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x03 0x03]
  Connection: 9
     0x0e 0x12 0x0f 0x0b 0x0c* 0x0d 0x0a 0x10 0x11
Node 0x18 [Audio Selector] wcaps 0x300103: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x07 0x07]
  Connection: 1
     0x15
Node 0x19 [Audio Selector] wcaps 0x300103: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x0a 0x0a]
  Connection: 1
     0x16
Node 0x1a [Audio Selector] wcaps 0x300103: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x0b 0x0b]
  Connection: 1
     0x17
Node 0x1b [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x18 0x13* 0x14
Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x19* 0x13 0x14
Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x1a* 0x13 0x14
Node 0x1e [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x1f [Vendor Defined Widget] wcaps 0xf30201: Stereo Digital
  Delay: 3 samples
Node 0x20 [Audio Input] wcaps 0x140311: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
  Connection: 1
     0x22
Node 0x21 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x034410a0: [Jack] SPDIF Out at Ext Left
    Conn = RCA, Color = Black
    DefAssociation = 0xa, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Connection: 5
     0x1e* 0x1f 0x1b 0x1c 0x1d
Node 0x22 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x00010024: IN EAPD Detect
  EAPD 0x0:
  Pin Default 0x40f000f6: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x6
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 3 samples
Node 0x23 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=0
  Amp-Out vals:  [0x00]
Node 0x24 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=1, val=127
  Connection: 4
     0x02* 0x03 0x04 0x05
Codec: Conexant ID 2c06
Address: 1
Vendor Id: 0x14f12c06
Subsystem Id: 0x14f1000f
Revision Id: 0x100000
Modem Function Group: 0x2
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 7 Apr 30  2009 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 6 Apr 30  2009 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 5 Apr 30 03:26 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 4 Apr 30  2009 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 3 Apr 30  2009 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Apr 30  2009 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfe9fc000 irq 21'
  Mixer name	: 'SigmaTel STAC9228'
  Components	: 'HDA:83847616,10280227,00100201 HDA:14f12c06,14f1000f,00100000'
  Controls      : 37
  Simple ctrls  : 24
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 118 [93%] [-6.75dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 102 [80%] [-18.75dB] [on]
  Front Right: Playback 102 [80%] [-18.75dB] [on]
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
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 102 [80%] [-18.75dB] [on]
  Front Right: Playback 102 [80%] [-18.75dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Mic as Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'Digital Playback' 'ADAT' 'Analog Mux 1' 'Analog Mux 2' 'Analog Mux 3'
  Item0: 'Digital Playback'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 7 [50%] [10.50dB] [on]
  Front Right: Capture 7 [50%] [10.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 10 [71%] [15.00dB] [on]
  Front Right: Capture 10 [71%] [15.00dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 11 [79%] [16.50dB] [on]
  Front Right: Capture 11 [79%] [16.50dB] [on]
Simple mixer control 'Analog Loopback',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Digital Input Source',0
  Capabilities: enum
  Items: 'Analog Inputs' 'Digital Mic 1'
  Item0: 'Digital Mic 1'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 3 [75%] [30.00dB]
  Front Right: Capture 3 [75%] [30.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 3 [75%] [30.00dB]
  Front Right: Capture 3 [75%] [30.00dB]
Simple mixer control 'Mux',2
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 3 [75%] [30.00dB]
  Front Right: Capture 3 [75%] [30.00dB]
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [on]
Simple mixer control 'Swap Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		iface MIXER
		name 'Input Source'
		value Mic
	}
	control.2 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		iface MIXER
		name 'Input Source'
		index 1
		value Mic
	}
	control.3 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		iface MIXER
		name 'Input Source'
		index 2
		value Mic
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Analog Loopback'
		value false
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 14'
		comment.dbmin 0
		comment.dbmax 2100
		iface MIXER
		name 'Capture Volume'
		value.0 7
		value.1 7
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 14'
		comment.dbmin 0
		comment.dbmax 2100
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 10
		value.1 10
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 14'
		comment.dbmin 0
		comment.dbmax 2100
		iface MIXER
		name 'Capture Volume'
		index 2
		value.0 11
		value.1 11
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 2
		value.0 true
		value.1 true
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 102
		value.1 102
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 127
		value.1 127
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 127
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value true
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 127
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value true
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Swap Center/LFE Playback Switch'
		value false
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic as Output Switch'
		value false
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		comment.dbmin -1800
		comment.dbmax 0
		iface MIXER
		name 'PC Beep Playback Volume'
		value 0
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Beep Playback Switch'
		value true
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 102
		value.1 102
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 4'
		comment.dbmin 0
		comment.dbmax 4000
		iface MIXER
		name 'Mux Capture Volume'
		value.0 3
		value.1 3
	}
	control.26 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 4'
		comment.dbmin 0
		comment.dbmax 4000
		iface MIXER
		name 'Mux Capture Volume'
		index 1
		value.0 3
		value.1 3
	}
	control.27 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 4'
		comment.dbmin 0
		comment.dbmax 4000
		iface MIXER
		name 'Mux Capture Volume'
		index 2
		value.0 3
		value.1 3
	}
	control.28 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Analog Inputs'
		comment.item.1 'Digital Mic 1'
		iface MIXER
		name 'Digital Input Source'
		value 'Digital Mic 1'
	}
	control.29 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Digital Playback'
		comment.item.1 ADAT
		comment.item.2 'Analog Mux 1'
		comment.item.3 'Analog Mux 2'
		comment.item.4 'Analog Mux 3'
		iface MIXER
		name 'IEC958 Playback Source'
		value 'Digital Playback'
	}
	control.30 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.31 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.32 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.33 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.34 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value false
	}
	control.35 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 127'
		comment.dbmin -9525
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 118
	}
	control.36 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.37 {
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
nls_iso8859_1
vfat
fat
usb_storage
binfmt_misc
i915
drm
ppdev
lp
parport
bridge
stp
bnep
input_polldev
snd_hda_intel
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
psmouse
video
serio_raw
dcdbas
sdhci_pci
pcspkr
ieee80211_crypt_tkip
ricoh_mmc
iTCO_wdt
snd
intel_agp
sdhci
output
iTCO_vendor_support
joydev
soundcore
agpgart
wl
ieee80211_crypt
snd_page_alloc
squashfs
aufs
exportfs
nls_cp437
isofs
usbhid
ohci1394
ieee1394
tg3
fbcon
tileblit
font
bitblit
softcursor


```

---

### Post by peripatetic on 2009-04-30
Still no luck, having now spent most of two days on this. It strikes me that if I could find a way to completely remove alsa, pulseaudio and all associated files, plus config, and then reinstall it, this would solve the problem. However when trying to remove it, I see it will also take ubunutu-desktop with it, which would seem to be a bit of a problem.

---

### Post by peripatetic on 2009-05-01
Getting closer after two days of fiddling. Have discovered that the commented entries in /etc/modprobe.d/alsa-base.conf don't work and the model=dell is working best so far. 

#options snd-hda-intel model=laptop enable=1 index=0
#options snd_hda_intel model=3stack
#options snd-hda-intel model=3stack
#options snd_hda_intel model=dell-laptop
#options snd-hda-intel model=3stack
options snd-hda-intel model=dell
# Not tried yet:
# 5stack dell-3stack dell-bios ref

After rebooting with that AND running alsamixer -c 0 and unmuting any channels marked with MM, then I now get sound (although it seems quieter than usual). Microphone is still not working. 

Really, shouldn't this be a little easier ...

---

### Post by marconeuro on 2009-05-01
I have your same problem, same "HDA Intel, STAC92xx Analog" device, but your solution won't work so far, did you missed to mention some steps?

---

### Post by marconeuro on 2009-05-01
Found the solution for mine in another thread,
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by peripatetic on 2009-05-18
I got most of it working with 

options snd-hda-intel model=dell-3stack

placed in /etc/modprobe.d/alsa-base.conf

The external mic still doesn't work, but the internal one does. 
The center headphones jack doesn't switch off the internal speakers, but the left hand headphones jack does. 
Not perfect, but workable. 

I also upgraded alsa to version 1.19 and then to 1.20, but still the best solution was the dell-3stack one. 

Sorry I didn't reply earlier. It seems that the forum notifications aren't working for me.

---

### Post by peripatetic on 2009-07-30
Well after three months of limping along using only the internal mic, using Alsa 1.20, I did an update and now the mic has stopped working again. Both internal mic and Mic Jack are silent. 

I just don't have the patience to go through all this hassle every three months, or every kernel upgrade, or every time the wind is in the wrong direction. So, since Ubuntu 9.04, on laptop has sound which works for about 2 hours and then degenerates into a CPU consuming echoey mess. The other, the one this thread is about, has no mic, after spending 2 or 3 days fiddling. 

So. If I want to use Linux on a laptop, I can't expect sound then. This whole pulse, alsa, oss thing is a mess.

---

