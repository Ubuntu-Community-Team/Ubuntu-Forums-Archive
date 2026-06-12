---
title: "using multiple jacks with alsa and/or pulse"
date: 2010-05-05
forum: Hardware
---

### Post by joep-vd on 2010-05-05
Hey I have some desires relating to audio. I want to create a multi zone setup for music player daemon, and therefore I should be able to send different (or the same) audio to the different jack plugs I have on my machine. 

For one, I want to do most via the terminal, since I'm working with the Ubuntu 9.04 based distro CrunchBang. 

I use the onboard sound card of the AS-Rock N68-S motherboard. Two jack connections are assigned to get sound out, one on where to go the front and one on the back. And I'd appreciate some assistance with finding out how to call for these in mpd. 

Also, in the alsa mixer the sliders seem to be misnamed (there is no 'back' slider, Master doesn't do anything). 

And... I encountered somewhere somehow that on some hardware it is possible to reassign for example the line-in to a second output (as apparently with surround set-ups is done). 

Well, pointers forward are very appreciated...

---

### Post by techunit on 2010-05-05
I am going to have to try looking at this. I have two audio out jacks On my laptop so I am going to look at this and try to help if I can.

---

### Post by joep-vd on 2010-05-05
Coolness! That makes two on this endeavor! 

Perhaps a good starting point for me to see what is happening where is to fix the following: 

If I plug a jack in the front, then the audio on the back gets muted. Any way to make the jack in the front just copy the stream to the back?

---

### Post by lidex on 2010-05-05
This may be helpful:
[http://ubuntuforums.org/showthread.php?t=1005196]("http://ubuntuforums.org/showthread.php?t=1005196")

Have you considered jack?

---

### Post by joep-vd on 2010-05-06
Thanks for your reply, but I am not interested (yet) in recording sounds. I'd like to be able to relay some sound to an arbitrary hardware jack output. 

If I understood it correctly, the software JACK can relay sound output from one program to the input of another. I think I don't need this. I want to be able to connect a piece of software to an arbitrary hardware output. And I think JACK (software) cannot directly communicate with the hardware. 

I got this information from [this splendid overview of audio in linux]("http://www.techradar.com/news/audio/linux-audio-explained-685419").

---

### Post by joep-vd on 2010-05-06
I guess this could be useful for me or somebody else: I used the [alsa-info script]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh") that is in your sig, lidex. 

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Thu May  6 08:16:43 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!DMI Information
!!---------------

Manufacturer:      To Be Filled By O.E.M.
Product Name:      To Be Filled By O.E.M.


!!Kernel Information
!!------------------

Kernel release:    2.6.28-18-generic
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

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfbff8000 irq 21


!!PCI Soundcards installed in the system
!!--------------------------------------

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:05.0 0403: 10de:03f0 (rev a2)
	Subsystem: 1849:0397


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
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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

Codec: VIA VIA VT1708S
Address: 0
Vendor Id: 0x11064397
Subsystem Id: 0x18490397
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=1, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0
Node 0x10 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x28 0x28]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x13 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x9f 0x9f]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x17
Node 0x14 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x1e
Node 0x15 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x16 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x14 0x14] [0x17 0x17] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x97 0x97] [0x97 0x97]
  Power: setting=D0, actual=D0
  Connection: 7
     0x10 0x1f 0x1a 0x1b 0x1e 0x1d 0x25
Node 0x17 [Audio Selector] wcaps 0x300501: Stereo
  Power: setting=D0, actual=D0
  Connection: 6
     0x1f 0x1a* 0x1b 0x1e 0x1d 0x16
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Power: setting=D0, actual=D0
  Connection: 1
     0x11
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410110f0: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x18
Node 0x1a [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x01a19036: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x6
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x26
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00002334: IN OUT Detect
    Vref caps: HIZ 50 100
  Pin Default 0x0181303e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x3, Sequence = 0xe
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x18
Node 0x1c [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x0:
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x16
Node 0x1d [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000233c: IN OUT HP Detect
    Vref caps: HIZ 50 100
  Pin Default 0x0221411f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
    Misc = NO_PRESENCE
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=01, enabled=1
  Power: setting=D0, actual=D0
  Connection: 2
     0x16* 0x25
Node 0x1e [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000233c: IN OUT HP Detect
    Vref caps: HIZ 50 100
  Pin Default 0x02a19138: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x8
    Misc = NO_PRESENCE
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 2
     0x16* 0x25
Node 0x1f [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x90370137: [Fixed] CD at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x7
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power: setting=D0, actual=D0
Node 0x20 [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x474410f0: [N/A] SPDIF Out at Ext Rear Panel
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Power: setting=D0, actual=D0
  Connection: 1
     0x15
Node 0x22 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410160f0: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x26
Node 0x23 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x410120f0: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x27
Node 0x24 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x2a 0x2a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x2a, nsteps=0x2a, stepsize=0x05, mute=0
  Amp-Out vals:  [0x19 0x19]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x26 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Power: setting=D0, actual=D0
  Connection: 1
     0x24
Node 0x27 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Power: setting=D0, actual=D0
  Connection: 1
     0x25
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 6 May  6 09:05 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 5 May  6 10:02 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 4 May  6 09:06 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 3 May  6 09:05 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 May  6 09:05 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [NVidia]

Card hw:0 'NVidia'/'HDA NVidia at 0xfbff8000 irq 21'
  Mixer name	: 'VIA VIA VT1708S'
  Components	: 'HDA:11064397,18490397,00100000'
  Controls      : 24
  Simple ctrls  : 15
Simple mixer control 'Master Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 20 [65%] [-4.50dB] [on]
  Front Right: Playback 20 [65%] [-4.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 25 [60%] [-25.50dB] [on]
  Front Right: Playback 25 [60%] [-25.50dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 219 [86%] [-7.20dB]
  Front Right: Playback 219 [86%] [-7.20dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 40 [95%] [-3.00dB] [on]
  Front Right: Playback 40 [95%] [-3.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [off]
  Front Right: Capture 31 [100%] [30.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'OFF' 'ON'
  Item0: 'OFF'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Stereo Mixer' 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'


!!Alsactl output
!!-------------

--startcollapse--
state.NVidia {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Master Front Playback Volume'
		value.0 20
		value.1 20
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 42'
		comment.dbmin -6300
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 40
		value.1 40
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 42'
		comment.dbmin -6300
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 25
		value.1 25
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 true
		value.1 true
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 true
		value.1 true
	}
	control.11 {
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
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 true
		value.1 true
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 23
		value.1 23
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 OFF
		comment.item.1 ON
		iface MIXER
		name 'Independent HP'
		value OFF
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1650
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		value.0 31
		value.1 31
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1650
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
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
		name 'Mic Boost Capture Volume'
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
		name 'Front Mic Boost Capture Volume'
		value.0 0
		value.1 0
	}
	control.22 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Stereo Mixer'
		comment.item.1 Mic
		comment.item.2 'Front Mic'
		comment.item.3 Line
		comment.item.4 CD
		iface MIXER
		name 'Input Source'
		value Mic
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
		value.0 219
		value.1 219
	}
	control.24 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 120'
		comment.tlv '0000000100000008fffff44800000032'
		comment.dbmin -3000
		comment.dbmax 3000
		iface MIXER
		name 'Digital Capture Volume'
		value.0 60
		value.1 60
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
bridge
stp
bnep
vboxnetadp
vboxnetflt
vboxdrv
input_polldev
video
output
ipt_REJECT
ipt_LOG
xt_limit
xt_tcpudp
xt_state
ipt_addrtype
ip6table_filter
ip6_tables
nf_nat_irc
nf_conntrack_irc
nf_nat_ftp
nf_nat
nf_conntrack_ipv4
nf_defrag_ipv4
nf_conntrack_ftp
nf_conntrack
iptable_filter
ip_tables
x_tables
lp
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
snd
nvidia
psmouse
btusb
soundcore
i2c_nforce2
agpgart
pcspkr
serio_raw
ppdev
usbhid
snd_page_alloc
parport_pc
parport
forcedeth
fbcon
tileblit
font
bitblit
softcursor
compcache
lzo_decompress
lzo_compress
tlsf


!!ALSA/HDA dmesg
!!------------------

[    8.321253] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[    8.321259] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[    8.321326] HDA Intel 0000:00:05.0: setting latency timer to 64
[    8.971684] lp0: using parport0 (interrupt-driven).



```

---

### Post by lidex on 2010-05-06
Nicely written piece. Did you check the link I provided? That was not for Jack.

---

### Post by joep-vd on 2010-05-06
Yeah I reread your link now, but it is of limited importance to me, since PulseAudio works. It pointed me to padevchooser and pavucontrol. But for now, I could select different sound cards. But I would need to call for the different subdevices on the one sound card I have. See the aplay output from the script. 

Maybe as a pointer: Where is the hot-plug feature controlled? That seems related...

---

### Post by joep-vd on 2010-05-06
Did I get something in my mind that is plainly impossible? Can I use one sound card to process two different sound streams to two physical output, or is the only option one of acquiring another piece of hardware?

---

### Post by joep-vd on 2010-05-07
Sorry that I keep replying to myself... It's an ongoing discovery route, and since these threads have been helping me so much, I think it doesn't hurt... 

I suddenly recall that I could use the two plugs independently as described under Windows with the device drivers installed. So it should be possible from a hardware point of view. 

...only how to call for these different outputs... :confused:

---

### Post by joep-vd on 2010-05-11
I figured it out, though with the help of new (old) hardware. 

Have now two instances of mpd running, both referring to two sinks in pulse, and I can select to play the output to any of the two sinks from within my favorite client.

---

