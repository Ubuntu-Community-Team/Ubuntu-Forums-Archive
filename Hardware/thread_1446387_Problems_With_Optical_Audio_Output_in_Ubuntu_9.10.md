---
title: "Problems With Optical Audio Output in Ubuntu 9.10"
date: 2010-04-04
forum: Hardware
---

### Post by ltpg97 on 2010-04-04
Greetings,

I'm kind of new to Ubuntu and I just installed a new audio card in my computer running Ubuntu 9.10. The Audio card is a Diamond Xtreme XS71DDL. I have the Optical Audio Output connected to my Kenwood receiver but I am getting no 5.1 surround sound when I play DVD movies. In fact, I'm getting no sound at all. How do I configure Ubuntu to play sound with Optical Audio Output?

NOTE: The original audio card is an embedded into the motherboard.

---

### Post by ltpg97 on 2010-04-08
Does anyone have any answers? I guess not since no one has replied to my post.

---

### Post by cchhrriiss121212 on 2010-04-08
When installing a new sound card, you will first have to disable the on board sound through your bios menu (hit f2 before getting to grub).
Then you can see whether the new card is recognised by typing "aplay -l" into a terminal. You can set the sound levels of your new card using alsamixer.

---

### Post by lidex on 2010-04-08
Still not working? Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by DJ-phYre on 2010-04-09
> **lidex said:**
> Still not working? Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

I just bought a HTPC and am having the exact same problem with this exact card. I am using an optical cable to the back of my receiver. 

```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat Apr 10 02:56:09 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


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

snd_cmipci


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

 0 [CMI8768        ]: CMI8738-MC8 - C-Media CMI8768
                      C-Media CMI8768 at 0xb800, irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

05:04.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

05:04.0 0401: 13f6:0111 (rev 10)
	Subsystem: 13f6:0111


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

!!Module: snd_cmipci
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	fm_port : 904,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	joystick_port : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	mpu_port : 816,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	soft_ac3 : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 10 Apr  9 21:51 /dev/snd/controlC0
crw-rw----  1 root audio 116,  4 Apr  9 21:51 /dev/snd/midiC0D0
crw-rw----  1 root audio 116,  9 Apr  9 21:54 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  8 Apr  9 21:51 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  7 Apr  9 21:51 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  6 Apr  9 21:52 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116,  5 Apr  9 21:52 /dev/snd/pcmC0D2p
crw-rw----  1 root audio 116,  3 Apr  9 21:50 /dev/snd/seq
crw-rw----  1 root audio 116,  2 Apr  9 21:50 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Apr  9 21:51 .
drwxr-xr-x 3 root root 240 Apr  9 21:51 ..
lrwxrwxrwx 1 root root  12 Apr  9 21:51 pci-0000:05:04.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [CMI8768]

Card hw:0 'CMI8768'/'C-Media CMI8768 at 0xb800, irq 17'
  Mixer name	: 'CMedia PCI'
  Components	: ''
  Controls      : 41
  Simple ctrls  : 22
Simple mixer control 'Master',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%]
  Front Right: Playback 23 [74%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Front Left: Playback 255 [100%] [0.00dB] [on] Capture [off]
  Front Right: Playback 255 [100%] [0.00dB] [on] Capture [off]
Simple mixer control 'Synth',0
  Capabilities: pvolume pswitch pswitch-joined cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 17 [55%] [off] Capture [off]
  Front Right: Playback 17 [55%] [off] Capture [off]
Simple mixer control 'Line-In Mode',0
  Capabilities: enum
  Items: 'Line-In' 'Rear Output' 'Bass Output'
  Item0: 'Line-In'
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined cvolume cvolume-joined pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: Playback 0 - 31 Capture 0 - 7
  Mono: Playback 0 [0%] [off] Capture 0 [0%] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [on]
Simple mixer control 'Mic-In Mode',0
  Capabilities: enum
  Items: 'Mic-In' 'Center/LFE Output'
  Item0: 'Center/LFE Output'
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 0 [0%] [off]
Simple mixer control 'IEC958 5V',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Copyright',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Monitor',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Phase Inverse',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Select',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 In Valid',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Loop',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 2 [67%] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Four Channel Mode',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.CMI8768 {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Master Playback Volume'
		value.0 23
		value.1 23
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name '3D Control - Switch'
		value false
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PCM Capture Switch'
		value.0 false
		value.1 false
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Synth Playback Volume'
		value.0 25
		value.1 25
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Synth Playback Switch'
		value true
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 4
		iface MIXER
		name 'Synth Capture Route'
		value.0 false
		value.1 false
		value.2 false
		value.3 false
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 4
		iface MIXER
		name 'CD Capture Route'
		value.0 false
		value.1 false
		value.2 false
		value.3 false
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Line Playback Volume'
		value.0 17
		value.1 17
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 4
		iface MIXER
		name 'Line Capture Route'
		value.0 false
		value.1 false
		value.2 false
		value.3 false
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Mic Playback Volume'
		value 0
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value false
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Capture Switch'
		value false
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		iface MIXER
		name 'PC Speaker Playback Volume'
		value 2
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		iface MIXER
		name 'Aux Playback Volume'
		value.0 0
		value.1 0
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Aux Playback Switch'
		value.0 false
		value.1 false
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Aux Capture Switch'
		value.0 false
		value.1 false
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost Playback Switch'
		value false
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 7'
		iface MIXER
		name 'Mic Capture Volume'
		value 0
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 7'
		iface MIXER
		name 'Phone Playback Volume'
		value 0
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value false
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Speaker Playback Switch'
		value true
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost Capture Switch'
		value true
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Four Channel Mode'
		value true
	}
	control.28 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Line-In
		comment.item.1 'Rear Output'
		comment.item.2 'Bass Output'
		iface MIXER
		name 'Line-In Mode'
		value Line-In
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Output Switch'
		value false
	}
	control.30 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 In Valid'
		value false
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Copyright'
		value false
	}
	control.32 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 5V'
		value true
	}
	control.33 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Loop'
		value false
	}
	control.34 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 In Monitor'
		value false
	}
	control.35 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		device 2
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.36 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		device 2
		name 'IEC958 Playback Con Mask'
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.38 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 In Select'
		value false
	}
	control.39 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 In Phase Inverse'
		value false
	}
	control.40 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic-In
		comment.item.1 'Center/LFE Output'
		iface MIXER
		name 'Mic-In Mode'
		value 'Center/LFE Output'
	}
	control.41 {
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
snd_cmipci
gameport
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_page_alloc
snd_opl3_lib
snd_hwdep
snd_mpu401_uart
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
ppdev
snd_seq_midi_event
joydev
parport_pc
nvidia
asus_atk0110
snd_seq
snd_timer
snd_seq_device
snd
lp
parport
iptable_filter
soundcore
ip_tables
x_tables
ohci1394
usbhid
ieee1394
floppy
r8169
mii
intel_agp
agpgart


!!ALSA/HDA dmesg
!!------------------

```

---

### Post by pondo on 2010-07-15
Any Luck? I have the same card on my 10.04 machine. The card works, meaning the analog outputs work...but not the optical output... :-(
 
Is this card even worth bothering with?

---

