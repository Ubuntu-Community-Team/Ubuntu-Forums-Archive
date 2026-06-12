---
title: "Gateway NX200s Intel 82801DB-ich4 - NO SOUND"
date: 2012-01-10
forum: Hardware
---

### Post by AfterBerner on 2012-01-10
Help!

I've recently updated to 11.10 from 11.04.  My laptop sound worked fine under 11.04, but since the update it no longer works.  I've checked the boards as best I can so far, but no joy.  I've run the ALSA online check and here is the output:


!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Wed Jan 11 04:24:05 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 11.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.10"


!!DMI Information
!!---------------

Manufacturer:      Gateway
Product Name:      NX200S
Product Version:   1008574


!!Kernel Information
!!------------------

Kernel release:    3.0.0-14-generic
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

snd_intel8x0


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

 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:24c5 (rev 03)
	Subsystem: 161f:203e


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
snd-hda-intel: model=gateway
snd-hda-intel: enable_msi=1


!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
	ac97_clock : 0
	ac97_quirk : (null)
	buggy_irq : N
	buggy_semaphore : N
	enable : N
	id : (null)
	index : -1
	joystick : 0
	spdif_aclink : 0
	xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1981B

PCI Subsys Vendor: 0x161f
PCI Subsys Device: 0x203e

Flags: 10
Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         :  0dB [ 0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : Mic
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 SPDIF VRA
Extended status  : SPCV SPDIF=10/11 SPDIF VRA
PCM front DAC    : 44100Hz
PCM ADC          : 44100Hz
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=48kHz



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0090
0:02 = 0000
0:04 = 0000
0:06 = 801f
0:08 = 0000
0:0a = 0000
0:0c = 8003
0:0e = 0003
0:10 = 0303
0:12 = 0303
0:14 = 0000
0:16 = 0303
0:18 = 0808
0:1a = 0303
0:1c = 8e8e
0:1e = 0000
0:20 = 0200
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0605
0:2a = 0435
0:2c = ac44
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2824
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
0:5c = 4000
0:5e = 0000
0:60 = 8080
0:62 = 0000
0:64 = 8000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 1800
0:74 = 1001
0:76 = 2050
0:78 = 0000
0:7a = 0000
0:7c = 4144
0:7e = 5374
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  8 Jan 10 22:02 /dev/snd/controlC0
crw-rw----  1 root audio 116,  7 Jan 10 22:04 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  6 Jan 10 22:07 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  5 Jan 10 22:02 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116,  4 Jan 10 22:02 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116,  3 Jan 10 22:02 /dev/snd/pcmC0D3c
crw-rw----  1 root audio 116,  2 Jan 10 22:03 /dev/snd/pcmC0D4p
crw-rw----  1 root audio 116,  1 Jan 10 22:02 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Jan 10 22:02 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan 10 22:02 .
drwxr-xr-x 3 root root 240 Jan 10 22:02 ..
lrwxrwxrwx 1 root root  12 Jan 10 22:02 pci-0000:00:1f.5 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 1: Intel ICH - MIC ADC [Intel 82801DB-ICH4 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 2: Intel ICH - MIC2 ADC [Intel 82801DB-ICH4 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 3: Intel ICH - ADC2 [Intel 82801DB-ICH4 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [I82801DBICH4]

Card hw:0 'I82801DBICH4'/'Intel 82801DB-ICH4 with AD1981B at irq 17'
  Mixer name	: 'Analog Devices AD1981B'
  Components	: 'AC97a:41445374'
  Controls      : 34
  Simple ctrls  : 23
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 28 [90%] [7.50dB] [on] Capture [off]
  Front Right: Playback 28 [90%] [7.50dB] [on] Capture [off]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 28 [90%] [7.50dB] [on] Capture [off]
  Front Right: Playback 28 [90%] [7.50dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 28 [90%] [7.50dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost ( 20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 28 [90%] [7.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'AC-Link' 'A/D Converter'
  Item0: 'AC-Link'
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 28 [90%] [7.50dB] [on] Capture [on]
  Front Right: Playback 28 [90%] [7.50dB] [on] Capture [on]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mic'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 14 [93%] [21.00dB] [off]
  Front Right: Capture 14 [93%] [21.00dB] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.I82801DBICH4 {
	control.1 {
		iface MIXER
		name 'Master Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.2 {
		iface MIXER
		name 'Master Playback Volume'
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
	control.3 {
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
	control.4 {
		iface MIXER
		name 'Headphone Playback Volume'
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
	control.5 {
		iface MIXER
		name 'Master Mono Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface MIXER
		name 'Master Mono Playback Volume'
		value 0
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -4650
			dbmax 0
			dbvalue.0 -4650
		}
	}
	control.7 {
		iface MIXER
		name 'Phone Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.8 {
		iface MIXER
		name 'Phone Playback Volume'
		value 28
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 750
		}
	}
	control.9 {
		iface MIXER
		name 'Mic Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.10 {
		iface MIXER
		name 'Mic Playback Volume'
		value 28
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 750
		}
	}
	control.11 {
		iface MIXER
		name 'Mic Boost ( 20dB)'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.12 {
		iface MIXER
		name 'Line Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.13 {
		iface MIXER
		name 'Line Playback Volume'
		value.0 28
		value.1 28
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 750
			dbvalue.1 750
		}
	}
	control.14 {
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.15 {
		iface MIXER
		name 'CD Playback Volume'
		value.0 28
		value.1 28
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 750
			dbvalue.1 750
		}
	}
	control.16 {
		iface MIXER
		name 'Aux Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.17 {
		iface MIXER
		name 'Aux Playback Volume'
		value.0 28
		value.1 28
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 750
			dbvalue.1 750
		}
	}
	control.18 {
		iface MIXER
		name 'PCM Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.19 {
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
	control.20 {
		iface MIXER
		name 'Capture Source'
		value.0 Aux
		value.1 Aux
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
	control.21 {
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
	control.22 {
		iface MIXER
		name 'Capture Volume'
		value.0 14
		value.1 14
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 15'
			dbmin 0
			dbmax 2250
			dbvalue.0 2100
			dbvalue.1 2100
		}
	}
	control.23 {
		iface MIXER
		name 'Mono Output Select'
		value Mic
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Mix
			item.1 Mic
		}
	}
	control.24 {
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
	control.25 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.26 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.27 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.28 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.29 {
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
	control.30 {
		iface MIXER
		name 'IEC958 Playback Source'
		value AC-Link
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 AC-Link
			item.1 'A/D Converter'
		}
	}
	control.31 {
		iface MIXER
		name 'Stereo Mic'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.32 {
		iface MIXER
		name 'Headphone Jack Sense'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.33 {
		iface MIXER
		name 'Line Jack Sense'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.34 {
		iface MIXER
		name 'External Amplifier'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
michael_mic
arc4
lib80211_crypt_tkip
bnep
rfcomm
bluetooth
parport_pc
ppdev
binfmt_misc
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
i915
snd_timer
snd_seq_device
pcmcia
ipw2200
drm_kms_helper
libipw
tifm_sd
tifm_7xx1
tifm_core
joydev
drm
cfg80211
snd
yenta_socket
pcmcia_rsrc
pcmcia_core
soundcore
lib80211
i2c_algo_bit
snd_page_alloc
psmouse
serio_raw
shpchp
video
lp
parport
firewire_ohci
b44
firewire_core
crc_itu_t
ssb


!!ALSA/HDA dmesg
!!------------------




Being a UBUNTU nube this is pretty much greek to me past the first couple of sections.  I've tried the settings through the terminal ALSA interface...no joy.  I can get to the settings at the top interface, but it will not stay on "analog output (LFE)/no amplification" at all.  Please help!:confused:

---

### Post by AfterBerner on 2012-01-12
I've also been running another diagnostic:


Advanced Linux Sound Architecture Driver Version 1.0.24.
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 17
  1:        : sequencer
  2: [ 0- 4]: digital audio playback
  3: [ 0- 3]: digital audio capture
  4: [ 0- 2]: digital audio capture
  5: [ 0- 1]: digital audio capture
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0]   : control
 33:        : timer
cat: /proc/asound/hwdep: No such file or directory
00-00: Intel ICH : Intel 82801DB-ICH4 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801DB-ICH4 - MIC ADC : capture 1
00-02: Intel ICH - MIC2 ADC : Intel 82801DB-ICH4 - MIC2 ADC : capture 1
00-03: Intel ICH - ADC2 : Intel 82801DB-ICH4 - ADC2 : capture 1
00-04: Intel ICH - IEC958 : Intel 82801DB-ICH4 - IEC958 : playback 1
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for ryan: 
rm: cannot remove `/etc/asound.conf': No such file or directory
rm: cannot remove `/home/ryan/.asound*': No such file or directory
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
aptitude set to manually installed.
The following packages were automatically installed and are no longer required:
  libswscale2 libxvidcore4 linux-headers-3.0.0-12 libopenjpeg2 libpostproc52
  libvo-aacenc0 libavcodec-extra-53 libavutil-extra-51 libvo-amrwbenc0
  libavformat-extra-53 libboost-iostreams1.42.0 linux-headers-3.0.0-12-generic
  libva1 liboil0.3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
No candidate version found for padevchooser
No candidate version found for padevchooser
The following NEW packages will be installed:
  gnome-alsamixer libglademm-2.4-1c2a{a} paman pavucontrol{a} pavumeter{a} 
The following packages will be REMOVED:
  libavcodec-extra-53{u} libavformat-extra-53{u} libavutil-extra-51{u} 
  libboost-iostreams1.42.0{u} liboil0.3{u} libopenjpeg2{u} libpostproc52{u} 
  libswscale2{u} libva1{u} libvo-aacenc0{u} libvo-amrwbenc0{u} 
  libxvidcore4{u} linux-headers-3.0.0-12{u} 
  linux-headers-3.0.0-12-generic{u} 
0 packages upgraded, 5 newly installed, 14 to remove and 0 not upgraded.
Need to get 334 kB of archives. After unpacking 115 MB will be freed.
Do you want to continue? [Y/n/?] y
Get: 1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/universe gnome-alsamixer i386 0.9.7~cvs.20060916.ds.1-2.1ubuntu0.1 [51.4 kB]
Get: 2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libglademm-2.4-1c2a i386 2.6.7-2build1 [21.8 kB]
Get: 3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe paman i386 0.9.4-1ubuntu2 [92.2 kB]
Get: 4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe pavucontrol i386 0.99.1-0ubuntu1 [140 kB]
Get: 5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe pavumeter i386 0.9.3-1ubuntu1 [29.2 kB]
Fetched 334 kB in 1s (220 kB/s)
(Reading database ... 242630 files and directories currently installed.)
Removing libavformat-extra-53 ...
Removing libavcodec-extra-53 ...
Removing libswscale2 ...
Removing libpostproc52 ...
Removing libavutil-extra-51 ...
Removing libboost-iostreams1.42.0 ...
Removing liboil0.3 ...
Removing libopenjpeg2 ...
Removing libva1 ...
Removing libvo-aacenc0 ...
Removing libvo-amrwbenc0 ...
Removing libxvidcore4 ...
Removing linux-headers-3.0.0-12-generic ...
Removing linux-headers-3.0.0-12 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package gnome-alsamixer.
(Reading database ... 220930 files and directories currently installed.)
Unpacking gnome-alsamixer (from .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2.1ubuntu0.1_i386.deb) ...
Selecting previously deselected package libglademm-2.4-1c2a.
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.7-2build1_i386.deb) ...
Selecting previously deselected package paman.
Unpacking paman (from .../paman_0.9.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package pavucontrol.
Unpacking pavucontrol (from .../pavucontrol_0.99.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package pavumeter.
Unpacking pavumeter (from .../pavumeter_0.9.3-1ubuntu1_i386.deb) ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up gnome-alsamixer (0.9.7~cvs.20060916.ds.1-2.1ubuntu0.1) ...
Setting up libglademm-2.4-1c2a (2.6.7-2build1) ...
Setting up paman (0.9.4-1ubuntu2) ...
Setting up pavucontrol (0.99.1-0ubuntu1) ...
Setting up pavumeter (0.9.3-1ubuntu1) ...
Processing triggers for menu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
H/W path           Device      Class          Description
=========================================================
                               system         Notebook
/0                             bus            Motherboard
/0/0                           memory         98KiB BIOS
/0/4                           processor      Intel(R) Celeron(R) M processor   
/0/4/8                         memory         16KiB L1 cache
/0/4/9                         memory         1MiB L2 cache
/0/15                          memory         1280MiB System Memory
/0/15/0                        memory         256MiB SODIMM DDR Synchronous
/0/15/1                        memory         1GiB SODIMM DDR Synchronous
/0/100                         bridge         82852/82855 GM/GME/PM/GMV Processo
/0/100/0.1                     generic        82852/82855 GM/GME/PM/GMV Processo
/0/100/0.3                     generic        82852/82855 GM/GME/PM/GMV Processo
/0/100/2                       display        82852/855GM Integrated Graphics De
/0/100/2.1                     display        82852/855GM Integrated Graphics De
/0/100/1d                      bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1d.1                    bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1d.2                    bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1d.7                    bus            82801DB/DBM (ICH4/ICH4-M) USB2 EHC
/0/100/1e                      bridge         82801 Mobile PCI Bridge
/0/100/1e/7                    bridge         PCIxx21/x515 Cardbus Controller
/0/100/1e/7.2                  bus            OHCI Compliant IEEE 1394 Host Cont
/0/100/1e/7.3                  storage        PCIxx21 Integrated FlashMedia Cont
/0/100/1e/8        eth1        network        BCM4401 100Base-T
/0/100/1e/9        eth0        network        PRO/Wireless 2200BG [Calexico2] Ne
/0/100/1f                      bridge         82801DBM (ICH4-M) LPC Interface Br
/0/100/1f.1        scsi0       storage        82801DBM (ICH4-M) IDE Controller
/0/100/1f.1/0      /dev/sda    disk           40GB HTS424040M9AT00
/0/100/1f.1/0/1    /dev/sda1   volume         27GiB EXT4 volume
/0/100/1f.1/0/2    /dev/sda2   volume         959MiB Extended partition
/0/100/1f.1/0/2/5  /dev/sda5   volume         959MiB Linux swap / Solaris partit
/0/100/1f.1/0/3    /dev/sda3   volume         8582MiB EXT4 volume
/0/100/1f.1/1      /dev/cdrom  disk           RW/DVD GCC-4243N
/0/100/1f.3                    bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1f.5                    multimedia     82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1f.6                    communication  82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/1                             system         
total 0
crw-rw----+  1 root audio 116, 33 2012-01-12 19:06 timer
crw-rw----+  1 root audio 116,  1 2012-01-12 19:06 seq
crw-rw----+  1 root audio 116,  4 2012-01-12 19:06 pcmC0D2c
crw-rw----+  1 root audio 116,  5 2012-01-12 19:06 pcmC0D1c
crw-rw----+  1 root audio 116,  3 2012-01-12 19:06 pcmC0D3c
crw-rw----+  1 root audio 116,  8 2012-01-12 19:06 controlC0
drwxr-xr-x   2 root root       60 2012-01-12 19:06 by-path
drwxr-xr-x   3 root root      240 2012-01-12 19:06 .
crw-rw----+  1 root audio 116,  2 2012-01-12 19:06 pcmC0D4p
crw-rw----+  1 root audio 116,  7 2012-01-12 19:08 pcmC0D0c
crw-rw----+  1 root audio 116,  6 2012-01-12 19:09 pcmC0D0p
drwxr-xr-x  15 root root     4180 2012-01-12 19:19 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
02:07.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
02:07.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
02:07.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
02:08.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:09.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
/sbin/alsactl
Cannot stat /dev/dsp: Bad address
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  ryan       1533 F.... pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*.
[    0.000000] Found optimal setting for mtrr clean up
[    0.080524] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.083825] ACPI: No dock devices found.
[    0.083828] HEST: Table not found.
[    0.105793] pnp: PnP ACPI: found 8 devices
[    0.148952] audit: initializing netlink socket (disabled)
[    0.148972] type=2000 audit(1326416742.144:1): initialized
[    0.293921] ERST: Table is not found!
[    0.363620] Fixed MDIO Bus: probed
[    0.388417] hub 1-0:1.0: USB hub found
[    0.389065] hub 2-0:1.0: USB hub found
[    0.389432] hub 3-0:1.0: USB hub found
[    0.389815] hub 4-0:1.0: USB hub found
[    0.867818] isapnp: No Plug & Play device found
[    1.142491] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.452327] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[    1.452337] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[    1.452344] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
[    1.492331] ssb: Sonics Silicon Backplane found on PCI device 0000:02:08.0
[   14.529503] lp: driver loaded but no devices found
[   16.654813] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   18.638113] yenta_cardbus 0000:02:07.0: CardBus bridge found [161f:203e]
[   18.868837] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: excluding 0x3000-0x30ff 0x3400-0x34ff
[   18.874430] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0200000-0xe02fffff: excluding 0xe0200000-0xe020ffff
[   18.874454] pcmcia_socket pcmcia_socket0: cs: memory probe 0x50000000-0x53ffffff: excluding 0x50000000-0x53ffffff
[   20.754427] type=1400 audit(1326416764.109:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=566 comm="apparmor_parser"
[   20.755157] type=1400 audit(1326416764.109:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=566 comm="apparmor_parser"
[   20.755622] type=1400 audit(1326416764.109:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=566 comm="apparmor_parser"
[   20.756467] type=1400 audit(1326416764.113:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=551 comm="apparmor_parser"
[   20.757186] type=1400 audit(1326416764.113:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=551 comm="apparmor_parser"
[   20.757641] type=1400 audit(1326416764.113:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=551 comm="apparmor_parser"
[   22.183918] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   22.185650] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   22.186389] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   22.187005] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   22.187679] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xfffff
[   22.187762] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   22.187842] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   22.187926] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   24.804041] intel8x0_measure_ac97_clock: measured 55415 usecs (2670 samples)
[   31.049100] type=1400 audit(1326416774.405:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=783 comm="apparmor_parser"
[   31.049991] type=1400 audit(1326416774.405:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=783 comm="apparmor_parser"
[   34.938537] type=1400 audit(1326416778.293:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=817 comm="apparmor_parser"
[   35.000498] type=1400 audit(1326416778.357:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=822 comm="apparmor_parser"
[   35.005097] type=1400 audit(1326416778.361:12): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=823 comm="apparmor_parser"
[   35.005847] type=1400 audit(1326416778.361:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=823 comm="apparmor_parser"
[   35.006310] type=1400 audit(1326416778.361:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=823 comm="apparmor_parser"
[   36.287602] type=1400 audit(1326416779.641:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=824 comm="apparmor_parser"
[   36.298876] type=1400 audit(1326416779.653:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=824 comm="apparmor_parser"
[   36.306079] type=1400 audit(1326416779.661:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=824 comm="apparmor_parser"
[   36.657447] type=1400 audit(1326416780.013:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=831 comm="apparmor_parser"
[   36.859479] type=1400 audit(1326416780.213:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=832 comm="apparmor_parser"
[   36.860513] type=1400 audit(1326416780.217:20): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=832 comm="apparmor_parser"
[   36.866761] type=1400 audit(1326416780.221:21): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=833 comm="apparmor_parser"
[   36.867692] type=1400 audit(1326416780.221:22): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=833 comm="apparmor_parser"
[   37.034962] type=1400 audit(1326416780.389:23): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=834 comm="apparmor_parser"
sudo: /etc/init.d/sl-modem-daemon: command not found
/etc/modprobe.d/alsa-base.conf:options snd-hda-intel model=gateway
/etc/modprobe.d/alsa-base.conf~:options snd-hda-intel model=gateway
	Release Date: 07/21/2005
	Manufacturer: Gateway
	Product Name: NX200S
	Serial Number: 0035872411
	Manufacturer: Gateway
	Product Name:                             
	Serial Number: V52NM5500708RC600X
	Manufacturer: Gateway
	Serial Number: None
	Manufacturer: Intel
	Serial Number: Not Specified
	Port Type: Serial Port 16550A Compatible
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Manufacturer Name: Intel
snd_seq_dummy          12686  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Unloading ALSA sound driver modules: snd-seq-dummy snd-intel8x0 snd-ac97-codec snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-intel8x0 snd-ac97-codec snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-intel8x0 snd-ac97-codec snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
  *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:17 ioport:1c00(size=256) ioport:18c0(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff





I'm just trying to get sound out of the built in speakers of this laptop - which worked under 11.04.  I've tried all the recommended runnings online, but I can not get it to work yet.

---

