---
title: "Intel PantherPoint HDMI  audio card model"
date: 2014-02-22
forum: Hardware
---

### Post by moje_meno2000 on 2014-02-22
How can I find my audio card model? When I type 
cat /proc/asound/card0/codec* | grep Codec
I get this two:
Codec: IDT ID 7695
Codec: Intel PantherPoint HDMI

But I can't find this Codecs in :
[http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD#l2](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD#l2)
or in
alsa database on my computer.

How can I determinate my audio model?

Thanks.

---

### Post by Yellow Pasque on 2014-02-22
```
sudo update-pciids
lspci -v
```

---

### Post by moje_meno2000 on 2014-03-02
OK I got this:

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device fa30
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at d3510000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

but I still do not know to find what should i put at the end of my 
/etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=?????

Any qlue?

---

### Post by Yellow Pasque on 2014-03-02
> but I still do not know to find what should i put at the end of my
/etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=?????

That's probably not the solution to your issue. By the way, what exactly is your issue?
Please give entire info (I should have asked for it in last post, sorry):  [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by moje_meno2000 on 2014-03-09
Ok here it is: [http://www.alsa-project.org/db/?f=3c36625e7d2002f4b487681daf888536923a9986](http://www.alsa-project.org/db/?f=3c36625e7d2002f4b487681daf888536923a9986)
I have two problems and I think both are relateted with not having appropriate sound drivers.
1. problem: when I pull in headset I can hear sound over headset but I can hear sound also over laptop internal speakers.
I played around with gnome alsa mixer but no solution. I can disable it simultaniously but not separatly.
2. problem: my internal microphon is not working, only external works.

I realy appreciate you help.

---

### Post by moje_meno2000 on 2014-03-09
Here is full text of my system once again:

!!################################
!!ALSA Information Script v 0.4.63
!!################################

!!Script ran on: Sun Mar  9 08:41:47 UTC 2014


!!Linux Distribution
!!------------------

Ubuntu 12.04.4 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.4 LTS)"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      SATELLITE C50-A-15G
Product Version:   PSCGAE-03400XGR
Firmware Version:  1.00


!!Kernel Information
!!------------------

Kernel release:    3.8.0-36-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.8.0-36-generic
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xd3510000 irq 45


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:1e20 (rev 04)
	Subsystem: 1179:fa30


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
snd-hda-intel: model=auto
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
snd-hda-intel: model=auto


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : auto,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : Y


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: IDT ID 7695
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x111d7695
Subsystem Id: 0x1179fa30
Revision Id: 0x100101
No Modem Function Group found
Default PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=4, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x0a [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0421401f: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Power states: 
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x0b [Pin Complex] wcaps 0x400483: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x03 0x03]
  Pincap 0x00011724: IN EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x04a19040: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states: 
  Power: setting=D0, actual=D0
Node 0x0c [Pin Complex] wcaps 0x400483: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00011724: IN EAPD Detect
    Vref caps: HIZ 50 GRD 80
  EAPD 0x2: EAPD
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states: 
  Power: setting=D0, actual=D0
Node 0x0d [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00010050: OUT EAPD Balanced
  EAPD 0x2: EAPD
  Pin Default 0xd9130110: [Both] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states: 
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x0e [Pin Complex] wcaps 0x400403: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0xd9a30120: [Both] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states: 
  Power: setting=D0, actual=D0
Node 0x0f [Pin Complex] wcaps 0x400403: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states: 
  Power: setting=D0, actual=D0
Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="HDA Generic", type="Audio", device=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7a 0x7a]
  Converter: stream=8, channel=0
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Converter: stream=0, channel=0
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x12 [Audio Input] wcaps 0x1d0541: Stereo
  Device: name="HDA Generic", type="Audio", device=0
  Converter: stream=4, channel=0
  SDI-Select: 0
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x14
  Processing caps: benign=0, ncoeff=0
Node 0x13 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x15
  Processing caps: benign=0, ncoeff=0
Node 0x14 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-Out vals:  [0x1e 0x1e]
  Power states: 
  Power: setting=D0, actual=D0
  Connection: 5
     0x16* 0x10 0x11 0x0e 0x0f
Node 0x15 [Audio Selector] wcaps 0x300d0d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-Out vals:  [0x90 0x90]
  Power states: 
  Power: setting=D0, actual=D0
  Connection: 5
     0x16* 0x10 0x11 0x0e 0x0f
Node 0x16 [Audio Selector] wcaps 0x300501: Stereo
  Power states: 
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c 0x0b*
Node 0x17 [Audio Output] wcaps 0x4061d: Stereo Digital Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x18 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states: 
  Power: setting=D0, actual=D0
  Connection: 1
     0x17
Node 0x19 [Beep Generator Widget] wcaps 0x70040c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
  Power states: 
  Power: setting=D0, actual=D0
Node 0x1a [Vendor Defined Widget] wcaps 0xf00001: Stereo
Codec: Intel PantherPoint HDMI
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x80862806
Subsystem Id: 0x1179fa30
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x80]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560010: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x80]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560020: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x03
Node 0x07 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560030: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x04
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T  1 root audio 116,  7 Mar  9 09:31 /dev/snd/controlC0
crw-rw---T  1 root audio 116,  6 Mar  9 09:31 /dev/snd/hwC0D0
crw-rw---T  1 root audio 116,  5 Mar  9 09:31 /dev/snd/hwC0D3
crw-rw---T  1 root audio 116,  4 Mar  9 09:37 /dev/snd/pcmC0D0c
crw-rw---T  1 root audio 116,  3 Mar  9 09:37 /dev/snd/pcmC0D0p
crw-rw---T  1 root audio 116,  2 Mar  9 09:37 /dev/snd/pcmC0D3p
crw-rw---T  1 root audio 116,  1 Mar  9 09:31 /dev/snd/seq
crw-rw---T  1 root audio 116, 33 Mar  9 09:31 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Mar  9 09:31 .
drwxr-xr-x 3 root root 220 Mar  9 09:31 ..
lrwxrwxrwx 1 root root  12 Mar  9 09:31 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [PCH]

Card hw:0 'PCH'/'HDA Intel PCH at 0xd3510000 irq 45'
  Mixer name	: 'Intel PantherPoint HDMI'
  Components	: 'HDA:111d7695,1179fa30,00100101 HDA:80862806,1179fa30,00100000'
  Controls      : 12
  Simple ctrls  : 3
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 122 [96%] [-3.75dB] [on]
  Front Right: Playback 122 [96%] [-3.75dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [0.20dB]
  Front Right: Playback 254 [100%] [0.20dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.PCH {
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
		value.0 122
		value.1 122
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 127'
			dbmin -9525
			dbmax 0
			dbvalue.0 -375
			dbvalue.1 -375
		}
	}
	control.3 {
		iface PCM
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.4 {
		iface PCM
		name 'Capture Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.5 {
		iface CARD
		name 'HDMI/DP,pcm=3 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.7 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.8 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.9 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.10 {
		iface PCM
		device 3
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.11 {
		iface PCM
		device 3
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access 'read write'
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
	control.12 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 254
		value.1 254
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 -20
			dbvalue.1 -20
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
bnep
bbswitch
bluetooth
parport_pc
ppdev
snd_hda_codec_hdmi
snd_hda_codec_idt
snd_hda_intel
snd_hda_codec
nvidia
uvcvideo
coretemp
videobuf2_core
snd_hwdep
joydev
i915
kvm_intel
snd_pcm
videodev
arc4
snd_seq_midi
kvm
snd_rawmidi
snd_seq_midi_event
rtl8188ee
drm_kms_helper
snd_seq
videobuf2_vmalloc
snd_timer
videobuf2_memops
drm
snd_seq_device
i2c_algo_bit
snd
video
ghash_clmulni_intel
rtlwifi
cryptd
soundcore
sparse_keymap
mac80211
wmi
snd_page_alloc
alx
mdio
lp
mac_hid
psmouse
microcode
cfg80211
mei
parport
lpc_ich
serio_raw
usb_storage
hid_generic
usbhid
hid
ahci
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0a 0x0421401f
0x0b 0x04a19040
0x0c 0x40f000f0
0x0d 0xd9130110
0x0e 0xd9a30120
0x0f 0x40f000f0
0x18 0x40f000f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:

/sys/class/sound/hwC0D3/init_pin_configs:
0x05 0x58560010
0x06 0x58560020
0x07 0x18560030

/sys/class/sound/hwC0D3/driver_pin_configs:

/sys/class/sound/hwC0D3/user_pin_configs:

/sys/class/sound/hwC0D3/init_verbs:

/sys/class/sound/hwC0D3/hints:


!!ALSA/HDA dmesg
!!--------------

[    8.481860] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.20  Wed Oct 30 17:43:35 PDT 2013
[    8.482020] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    8.625992] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    8.803473] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off

---

### Post by Yellow Pasque on 2014-03-09
See: [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/235041](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/235041)

Basically, installing/running lts-saucy kernel should do it:
```
sudo update-pciids
sudo apt-get install linux-lts-saucy
```

---

### Post by Yellow Pasque on 2014-03-09
Oh, make sure you remove this line. It shouldn't be necessary:
```
options snd-hda-intel model=auto
```

---

