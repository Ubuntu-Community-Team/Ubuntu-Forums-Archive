---
title: "Headphones work but no sound on loudspeakers - Sony Vaio VGN-AR31E"
date: 2012-05-20
forum: Hardware
---

### Post by docalam on 2012-05-20
Hi guys -- need major help here, or atleast I think its major. Totally lost!! 

I have a sony Vaio VGN-AR31E and recently I got rid of windows as I got fed up of their control and them dictating what and how we can use our computers. Anyways - long story short

No Audio on loudspeakers -- but works fine with Headphones plugged in... 

No cam and hence cant get Video to work : /  thou the laptop comes with its own build in Sony MotionEye web cam.

I looked up seems many people have this problem but i cant seem to work it out :(

Need help!! 

Uploaded my Alsa script report :/
[http://www.alsa-project.org/db/?f=5f3ae6bca71da6578a73b0b061e6f1931ce0826f](http://www.alsa-project.org/db/?f=5f3ae6bca71da6578a73b0b061e6f1931ce0826f)



MANY THANKS!!!! 

Syed

---

### Post by docalam on 2012-05-20
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sun May 20 16:36:36 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 11.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.10"


!!DMI Information
!!---------------

Manufacturer:      Sony Corporation
Product Name:      VGN-AR31E
Product Version:   C3LNPYL8


!!Kernel Information
!!------------------

Kernel release:    3.0.0-19-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


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
                      HDA Intel at 0xd2300000 irq 47


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
	Subsystem: 104d:81fd


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
snd-hda-intel: model=auto position_fix=0
snd-hda-intel: model=auto position_fix=0
snd-hda-intel: model=auto position_fix=0


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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

Codec: SigmaTel CXD9872AKD
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x83847664
Subsystem Id: 0x104d1300
Revision Id: 0x100201
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=5, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=63
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="STAC92xx Analog", type="Audio", device=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x03 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Headphone Playback Volume", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=63
  Control: name="Headphone Playback Switch", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x04 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Converter: stream=0, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x05 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=63
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x06 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x07
  Processing caps: benign=0, ncoeff=0
Node 0x07 [Audio Selector] wcaps 0x300903: Stereo Amp-In R/L
  Amp-In caps: N/A
  Amp-In vals:  [0x80 0x80]
  Connection: 1
     0x0e
Node 0x08 [Audio Input] wcaps 0x1d0541: Stereo
  Device: name="STAC92xx Analog", type="Audio", device=0
  Converter: stream=1, channel=0
  SDI-Select: 0
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x09
  Processing caps: benign=0, ncoeff=0
Node 0x09 [Audio Selector] wcaps 0x300903: Stereo Amp-In R/L
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: N/A
  Amp-In vals:  [0x09 0x09]
  Connection: 1
     0x15
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000173c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x03211020: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x0b [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x0c [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x21211030: [Jack] HP Out at Sep Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x03
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Control: name="Mic Jack Mode", index=0, device=0
    ControlAmp: chs=0, dir=In, idx=0, ofs=0
  Pincap 0x0000173c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x03a15040: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Red
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x05
Node 0x10 [Audio Output] wcaps 0x40211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="STAC92xx Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x3e0]: 44100 48000 88200 96000 176400
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x11 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x03451150: [Jack] SPDIF Out at Ext Left
    Conn = Optical, Color = Black
    DefAssociation = 0x5, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 2
     0x10* 0x09
Node 0x12 [Audio Input] wcaps 0x140311: Stereo Digital
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
     0x13
Node 0x13 [Pin Complex] wcaps 0x440381: Stereo Digital
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Delay: 4 samples
  Connection: 1
     0x18
Node 0x14 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x90a7014e: [Fixed] Mic at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x4, Sequence = 0xe
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x15 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Mux Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 4
     0x0a 0x0d 0x14* 0x02
Node 0x16 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=0
  Amp-Out vals:  [0x00]
Node 0x17 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=0, val=127
  Connection: 4
     0x02 0x03 0x04 0x05
Node 0x18 [Audio Output] wcaps 0x40201: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  Delay: 4 samples
Codec: Conexant ID 2bfa
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x14f12bfa
Subsystem Id: 0x104d0200
Revision Id: 0x90000
Modem Function Group: 0x2
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  7 May 20 02:15 /dev/snd/controlC0
crw-rw----  1 root audio 116,  6 May 20 02:15 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  5 May 20 02:15 /dev/snd/hwC0D1
crw-rw----  1 root audio 116,  4 May 20 17:25 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  3 May 20 17:26 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  2 May 20 17:25 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  1 May 20 02:15 /dev/snd/seq
crw-rw----  1 root audio 116, 33 May 20 02:15 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May 20 02:15 .
drwxr-xr-x 3 root root 220 May 20 02:15 ..
lrwxrwxrwx 1 root root  12 May 20 02:15 pci-0000:00:1b.0 -> ../controlC0


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
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xd2300000 irq 47'
  Mixer name	: 'SigmaTel CXD9872AKD'
  Components	: 'HDA:83847664,104d1300,00100201 HDA:14f12bfa,104d0200,00090000'
  Controls      : 18
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',1
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
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
  Limits: Capture 0 - 15
  Front Left: Capture 9 [60%] [13.50dB] [on]
  Front Right: Capture 9 [60%] [13.50dB] [on]
Simple mixer control 'Mux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
	control.1 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -4800
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.2 {
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Headphone Playback Volume'
		index 1
		value.0 64
		value.1 64
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -4800
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.4 {
		iface MIXER
		name 'Headphone Playback Switch'
		index 1
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Mic Jack Mode'
		value 'Mic In'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Mic In'
			item.1 'Line In'
		}
	}
	control.6 {
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 64
		value.1 64
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -4800
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.7 {
		iface MIXER
		name 'Speaker Playback Switch'
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
		name 'Capture Volume'
		value.0 9
		value.1 9
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 15'
			dbmin 0
			dbmax 2250
			dbvalue.0 1350
			dbvalue.1 1350
		}
	}
	control.9 {
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.10 {
		iface MIXER
		name 'Mux Capture Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 4'
			dbmin 0
			dbmax 4000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.11 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.12 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.13 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.14 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.15 {
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.16 {
		iface MIXER
		name 'Master Playback Volume'
		value 64
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 64'
			dbmin -9999999
			dbmax 0
			dbvalue.0 0
		}
	}
	control.17 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.18 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
bnep
rfcomm
bluetooth
parport_pc
ppdev
vesafb
binfmt_misc
uvcvideo
videodev
joydev
snd_hda_codec_idt
nvidia
tifm_7xx1
tifm_core
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
arc4
snd_rawmidi
snd_seq_midi_event
iwl3945
snd_seq
iwl_legacy
snd_timer
snd_seq_device
pcmcia
mac80211
psmouse
cfg80211
snd
serio_raw
sony_laptop
soundcore
snd_page_alloc
yenta_socket
pcmcia_rsrc
pcmcia_core
video
lp
parport
ahci
libahci
e100
firewire_ohci
firewire_core
crc_itu_t


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0a 0x03211020
0x0b 0x411111f0
0x0c 0x21211030
0x0d 0x03a15040
0x0e 0x411111f0
0x0f 0x90170110
0x11 0x03451150
0x13 0x411111f0
0x14 0x90a7014e

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:
0x73 0x016a0000

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

---

### Post by docalam on 2012-05-20
help is much appreciated!!! 

THANK YOU!

Syed


p.s. please keep it simple

---

### Post by docalam on 2012-05-21
Anyone who knows how to fix or go about this problem - I would very much appreciate your help and input!! 

Thanks a million x

---

### Post by docalam on 2012-05-21
from what i have gathered -- device configured wrong and i need to switch them

Found hardware: "HDA-Intel" "SigmaTel CXD9872AKD" "HDA:83847664,104d1300,00100201 HDA:14f12bfa,104d0200,00090000" "0x104d" "0x81fd" Hardware is initialized using a generic method

but genome-alsamixer says I have SigmaTel CXD9872AKD ??? 

?? do i need to fix this to get the sound working properly -- or is there some other bug that needs correction to get the loudspeaker to work??

please help

---

### Post by docalam on 2012-05-24
I was and still am hoping someone would be able to help!

thanks

---

### Post by bencouve on 2012-06-19
I am having the same problem. Will post if I find a solution...

---

### Post by bencouve on 2012-06-20
Happy to say my sound is working now. I re-installed Ubuntu but the 64bit version and my internal speakers are now working. The headphones are working too. 

I had windows 7 installed on my laptop previously which is 64bit so not sure if this has something to do with it. Maybe try re-install with this version, if you have not already. Hope this has helped you.

---

### Post by wewantutopia on 2012-07-30
I to am having this EXACT same problem: sony VAIO sigmatel audio, sound from head phones but none from speakers.

Did anyone figure out a solution or does anyone have any suggestions??  

Thanks!

---

### Post by 24T on 2012-10-12
> **wewantutopia said:**
> I to am having this EXACT same problem: sony VAIO sigmatel audio, sound from head phones but none from speakers.

Did anyone figure out a solution or does anyone have any suggestions??  

Thanks!

Hello World,
My HW is VGN-AR31M, and it's the same case. I am looking for suggestions ):P

> Found hardware: "HDA-Intel" "SigmaTel CXD9872AKD" "HDA:83847664,104d1300,00100201 HDA:14f12bfa,104d0200,00090000" "0x104d" "0x81fd"
Hardware is initialized using a generic method

Webcam works fine after installing r5u87x driver
> Bus 001 Device 004: ID 05ca:1836 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]

I'd like watching TV some day :p and DVD one day later :lolflag:

Thanks for help !

---

