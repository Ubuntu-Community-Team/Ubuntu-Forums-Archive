---
title: "No Sound"
date: 2010-04-12
forum: Hardware
---

### Post by Madmoose on 2010-04-12
Hello all, 

My brother's girlfriend wanted to try out Ubuntu, so I installed it her HP G71-329WM laptop. 

Everything worked out of the box except the sound. I've tried many things here and there, and I still can't get it to work. 

Anyone have any ideas on a fix. I know I didn't give much information to start with, so ask and I'll send anything you want to know your way. 

Thanks,

---

### Post by Madmoose on 2010-04-13
bump

---

### Post by Madmoose on 2010-05-07
I'm going to bump this again, and supply you all with this information:

```
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Fri May  7 20:31:41 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP G71 Notebook PC


!!Kernel Information
!!------------------

Kernel release:    2.6.31-20-generic
Operating System:  GNU/Linux
Architecture:      x86_64
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

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd4500000 irq 29


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 103c:306b


!!Modprobe options (Sound related)
!!--------------------------------

snd-hda-intel: enable_msi=1
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
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 1
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

Codec: IDT 92HD75B2X5
Address: 0
Function Id: 0x1
Vendor Id: 0x111d7608
Subsystem Id: 0x103c306b
Revision Id: 0x100202
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=8, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[5]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[6]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[7]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Power-Map: 0x00
Analog Loopback: 0x00
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0121101f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Connection: 3
     0x10 0x11* 0x17
Node 0x0b [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01a11020: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
Node 0x0c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x92a71130: [Fixed] Mic at Int Front
    Conn = Analog, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x90110110: [Fixed] Speaker at Int N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10* 0x11 0x17
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x40f000f9: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x9
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
Node 0x0f [Vendor Defined Widget] wcaps 0xf00181: Stereo
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10 0x11 0x17*
Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x12 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x1c
  Processing caps: benign=0, ncoeff=0
Node 0x13 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x1d
  Processing caps: benign=0, ncoeff=0
Node 0x14 [Pin Complex] wcaps 0x400100: Mono
  Pincap 0x00000030: IN OUT
  Pin Default 0x40f000f1: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x1
  Pin-ctls: 0x00:
  Connection: 1
     0x16
Node 0x15 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x10 0x11 0x17*
Node 0x16 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x15
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x10 0x11 0x14 0x1a 0x1b
Node 0x18 [Pin Complex] wcaps 0x40000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40f000f2: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x2
  Pin-ctls: 0x00:
Node 0x19 [Vendor Defined Widget] wcaps 0xf0000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals: 
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 4
     0x1a* 0x17 0x18 0x19
Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 4
     0x1b* 0x17 0x18 0x19
Node 0x1e [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f4: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x4
  Pin-ctls: 0x00:
  Connection: 1
     0x24
Node 0x1f [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00010010: OUT EAPD
  EAPD 0x0:
  Pin Default 0x40f000f5: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x5
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 2
     0x24* 0x25
Node 0x20 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f6: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x6
  Pin-ctls: 0x00:
  Connection: 1
     0x25
Node 0x21 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x22 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x23 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x21* 0x1c 0x1d
Node 0x25 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x22* 0x1c 0x1d
Node 0x26 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Node 0x27 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=0, val=127
  Connection: 2
     0x10 0x11
Codec: LSI ID 1040
Address: 1
Function Id: 0x2
Vendor Id: 0x11c11040
Subsystem Id: 0x103c137e
Revision Id: 0x100200
Modem Function Group: 0x1
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 8 May  7 12:22 /dev/snd/controlC0
crw-rw----  1 root audio 116, 7 May  7 12:22 /dev/snd/hwC0D0
crw-rw----  1 root audio 116, 6 May  7 12:22 /dev/snd/hwC0D1
crw-rw----  1 root audio 116, 5 May  7 12:22 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 4 May  7 12:23 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 3 May  7 12:22 /dev/snd/seq
crw-rw----  1 root audio 116, 2 May  7 12:22 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May  7 12:22 .
drwxr-xr-x 3 root root 200 May  7 12:22 ..
lrwxrwxrwx 1 root root  12 May  7 12:22 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xd4500000 irq 29'
  Mixer name	: 'IDT 92HD75B2X5'
  Components	: 'HDA:111d7608,103c306b,00100202 HDA:11c11040,103c137e,00100200'
  Controls      : 28
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'DAC0',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'DAC1',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'Digital Input Source',0
  Capabilities: enum
  Items: 'Analog Inputs' 'Mixer'
  Item0: 'Analog Inputs'
Simple mixer control 'Digital Input Source',1
  Capabilities: enum
  Items: 'Analog Inputs' 'Mixer'
  Item0: 'Analog Inputs'
Simple mixer control 'Import0 Mux',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'Import1 Mux',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Import0 Mux Capture Switch'
		value.0 false
		value.1 false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Import0 Mux Capture Volume'
		value.0 23
		value.1 23
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Import1 Mux Capture Switch'
		value.0 false
		value.1 false
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Import1 Mux Capture Volume'
		value.0 23
		value.1 23
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'DAC0 Capture Switch'
		value.0 false
		value.1 false
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'DAC0 Capture Volume'
		value.0 23
		value.1 23
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'DAC1 Capture Switch'
		value.0 false
		value.1 false
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'DAC1 Capture Volume'
		value.0 23
		value.1 23
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 64
		value.1 64
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Mic In'
		comment.item.1 'Line In'
		iface MIXER
		name 'Mic Jack Mode'
		value 'Mic In'
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Beep Playback Switch'
		value false
	}
	control.17 {
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
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.20 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mux Capture Volume'
		value.0 0
		value.1 0
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mux Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.22 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		iface MIXER
		name 'Input Source'
		value Mic
	}
	control.23 {
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
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Analog Inputs'
		comment.item.1 Mixer
		iface MIXER
		name 'Digital Input Source'
		value 'Analog Inputs'
	}
	control.25 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Analog Inputs'
		comment.item.1 Mixer
		iface MIXER
		name 'Digital Input Source'
		index 1
		value 'Analog Inputs'
	}
	control.26 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 64
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.28 {
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
nls_utf8
isofs
binfmt_misc
ppdev
joydev
snd_hda_codec_idt
arc4
ecb
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
iptable_filter
ip_tables
x_tables
snd_seq
snd_timer
snd_seq_device
psmouse
serio_raw
ath9k
mac80211
led_class
ath
cfg80211
snd
soundcore
snd_page_alloc
lp
parport
fbcon
tileblit
font
bitblit
softcursor
r8169
mii
i915
drm
i2c_algo_bit
intel_agp
video
output


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0a 0x0121101f
0x0b 0x01a11020
0x0c 0x92a71130
0x0d 0x90110110
0x0e 0x40f000f9
0x14 0x40f000f1
0x18 0x40f000f2
0x1e 0x40f000f4
0x1f 0x40f000f5
0x20 0x40f000f6

/sys/class/sound/hwC0D0/driver_pin_configs:
0x0f 0x40f000f0
0x19 0x40f000f3

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[    3.287351] i2c-adapter i2c-2: unable to read EDID block.
[    3.287356] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    3.296241] [drm] fb0: inteldrmfb frame buffer device
--
[   15.768235]   alloc kstat_irqs on node 0
[   15.768242] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.768311]   alloc irq_desc for 29 on node 0
[   15.768313]   alloc kstat_irqs on node 0
[   15.768323] HDA Intel 0000:00:1b.0: irq 29 for MSI/MSI-X
[   15.768352] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.898758] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   15.962243] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   15.962312] input: HDA Intel HP Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.592005] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000
--
[   18.028600] i2c-adapter i2c-2: unable to read EDID block.
[   18.028605] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   18.036493] i2c-adapter i2c-2: unable to read EDID block.
[   18.036499] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   18.213093] i2c-adapter i2c-2: unable to read EDID block.
[   18.213099] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   18.219149] i2c-adapter i2c-2: unable to read EDID block.
[   18.219155] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.160644] i2c-adapter i2c-2: unable to read EDID block.
[   19.160648] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.165122] i2c-adapter i2c-2: unable to read EDID block.
[   19.165125] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.319372] i2c-adapter i2c-2: unable to read EDID block.
[   19.319378] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.324127] i2c-adapter i2c-2: unable to read EDID block.
[   19.324130] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.490430] i2c-adapter i2c-2: unable to read EDID block.
[   19.490434] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.494867] i2c-adapter i2c-2: unable to read EDID block.
[   19.494869] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.657869] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
--
[   37.567441] i2c-adapter i2c-2: unable to read EDID block.
[   37.567445] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   37.572198] i2c-adapter i2c-2: unable to read EDID block.
[   37.572201] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   37.757715] i2c-adapter i2c-2: unable to read EDID block.
[   37.757719] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   37.762419] i2c-adapter i2c-2: unable to read EDID block.
[   37.762422] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   37.918202] i2c-adapter i2c-2: unable to read EDID block.
[   37.918206] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   37.922895] i2c-adapter i2c-2: unable to read EDID block.
[   37.922898] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   38.983700] i2c-adapter i2c-2: unable to read EDID block.
[   38.983704] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   38.988135] i2c-adapter i2c-2: unable to read EDID block.
[   38.988137] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   42.630809] ISO 9660 Extensions: Microsoft Joliet Level 3



```

Also, 

I've noticed that I do get sound, but only out of the headphone jack. 

Any ideas?

Thanks

---

### Post by Madmoose on 2010-05-07
Found a fix here: [http://ubuntuforums.org/showthread.php?t=1341751&highlight=HP+G71+Sound+Problem](http://ubuntuforums.org/showthread.php?t=1341751&highlight=HP+G71+Sound+Problem)

---

