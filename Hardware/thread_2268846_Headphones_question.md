---
title: "Headphones question"
date: 2015-03-11
forum: Hardware
---

### Post by michael-piziak on 2015-03-11
Ubuntu 12.04 LTS

I plug my head phones in, and in the sound settings it switches from "speakers" to "headphone"

However, I can hear the speakers as well as the sound in the headphones.

How to turn the speaker off (built into the monitor) when headphones are plugged in ?

---

### Post by Yellow Pasque on 2015-03-11
It should mute automatically.
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by michael-piziak on 2015-03-12
> **Temüjin said:**
> It should mute automatically.
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Please tell me what those terminal commands will do if I type them in.

I found this thread where someone updated the Alsa driver and it solved the problem.  What could I type in or click to do that ?
[http://ubuntuforums.org/showthread.php?t=2212871&highlight=headphone+speaker](http://ubuntuforums.org/showthread.php?t=2212871&highlight=headphone+speaker)

---

### Post by Bucky Ball on 2015-03-12
How they did it is right [here]("http://ubuntuforums.org/showthread.php?t=2212871&p=12969411&viewfull=1#post12969411") in post #3. I would dig around a bit more before installing a PPA, though.

---

### Post by Yellow Pasque on 2015-03-12
> **michael-piziak said:**
> Please tell me what those terminal commands will do if I type them in

They delete everything on your hard disk..
Either that or they gather audio information and upload it to an easily shared link like so: [http://www.alsa-project.org/db/?f=cce86dbbeccdcf0f207840427e7012d97312d8ab](http://www.alsa-project.org/db/?f=cce86dbbeccdcf0f207840427e7012d97312d8ab)
Then someone like me looks at the info and sees what audio hardware you have and what kernel version you're running and whether updating the ALSA module would be a good idea. If so, I give you this link: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) , which points to the PPA you discovered in the last post.

---

### Post by michael-piziak on 2015-03-12
> **Temüjin said:**
> They delete everything on your hard disk..
Either that or they gather audio information and upload it to an easily shared link like so: [http://www.alsa-project.org/db/?f=cce86dbbeccdcf0f207840427e7012d97312d8ab](http://www.alsa-project.org/db/?f=cce86dbbeccdcf0f207840427e7012d97312d8ab)
Then someone like me looks at the info and sees what audio hardware you have and what kernel version you're running and whether updating the ALSA module would be a good idea. If so, I give you this link: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) , which points to the PPA you discovered in the last post.

That was funny.

I'm out of town now.  When I get back I'll enter that code into terminal and post back.

Thanks.

---

### Post by michael-piziak on 2015-03-24
> **Temüjin said:**
> It should mute automatically.
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

This is the ALSA information.

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Tue Mar 24 13:26:02 UTC 2015




!!Linux Distribution
!!------------------


Ubuntu 12.04.5 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.5 LTS)"




!!DMI Information
!!---------------


Manufacturer:      Hewlett-Packard
Product Name:      HP Compaq dc5800 Small Form Factor
Product Version:    
Firmware Version:  786F2 v01.55




!!Kernel Information
!!------------------


Kernel release:    3.13.0-46-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     k3.13.0-46-generic
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


 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf01a0000 irq 45




!!PCI Soundcards installed in the system
!!--------------------------------------


00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:1b.0 0403: 8086:293e (rev 02)
	Subsystem: 103c:281e




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
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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


Codec: Analog Devices AD1884
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x11d41884
Subsystem Id: 0x103c281e
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x7ff]: 8000 11025 16000 22050 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
State of AFG node 0x01:
  Power states:  D0 D3
  Power: setting=D0, actual=D0
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=1, dir=1, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x30311: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 3 samples
  Connection: 3
     0x01* 0x08 0x09
Node 0x03 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="AD1884 Alt Analog", type="Audio", device=2
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
  Amp-Out vals:  [0x27 0x27]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Control: name="PCM Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="AD1884 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=0
  Amp-Out vals:  [0x27 0x27]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x07 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x22 0x21
Node 0x08 [Audio Input] wcaps 0x100501: Stereo
  Device: name="AD1884 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x09 [Audio Input] wcaps 0x100501: Stereo
  Device: name="AD1884 Alt Analog", type="Audio", device=2
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x0a [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x21
Node 0x0b [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x0f 0x21
Node 0x0c [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
  Amp-Out vals:  [0x25 0x25]
  Connection: 5
     0x14* 0x15 0x16 0x20 0x25
Node 0x0d [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x27, nsteps=0x36, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 5
     0x14* 0x15 0x16 0x20 0x25
Node 0x0e [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x03 0x04*
Node 0x0f [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x03* 0x04
Node 0x10 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x8f]
Node 0x11 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Front Headphone Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001f: OUT HP Detect Trigger ImpSense
  Pin Default 0x02211030: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x07
Node 0x12 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="PCM Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Line Out Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001001f: OUT HP EAPD Detect Trigger ImpSense
  EAPD 0x0:
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x0a
Node 0x13 [Pin Complex] wcaps 0x40050c: Mono Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Speaker Phantom Jack", index=0, device=0
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1f]
  Pincap 0x00010010: OUT EAPD
  EAPD 0x2: EAPD
  Pin Default 0x99131150: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Black
    DefAssociation = 0x5, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x14 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x01 0x01]
  Pincap 0x00003727: IN Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a11040: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=03, enabled=1
Node 0x15 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Control: name="Line Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Line Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003727: IN Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01813020: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=04, enabled=1
Node 0x16 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
  Pin Default 0x599311f0: [N/A] Aux at Int ATAPI
    Conn = ATAPI, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0b
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x19 [Power Widget] wcaps 0x500500: Mono
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x20 0x21
Node 0x1a [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x591321f0: [N/A] Speaker at Int ATAPI
    Conn = ATAPI, Color = Grey
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1b [Pin Complex] wcaps 0x40030d: Stereo Digital Amp-Out
  Amp-Out caps: ofs=0x27, nsteps=0x27, stepsize=0x05, mute=1
  Amp-Out vals:  [0xa7 0xa7]
  Pincap 0x00000010: OUT
  Pin Default 0x414511f0: [N/A] SPDIF Out at Ext Rear
    Conn = Optical, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x02
Node 0x1c [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x41a191f0: [N/A] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x24
Node 0x1d [Vendor Defined Widget] wcaps 0xf00100: Mono
  Connection: 25
     0x07* 0x19 0x0a 0x0b 0x0c 0x0d 0x0e 0x0f 0x1a 0x1c 0x11 0x12 0x13 0x14 0x15 0x16 0x1e 0x1f 0x20 0x21 0x22 0x23 0x24 0x25 0x26
Node 0x1e [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x0e 0x21
Node 0x1f [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x1e
Node 0x20 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 5
     0x14 0x15 0x16 0x1a 0x25
Node 0x21 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 1
     0x20
Node 0x22 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x03* 0x04
Node 0x23 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x03* 0x04
Node 0x24 [Audio Mixer] wcaps 0x200103: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x23 0x21
Node 0x25 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 1
     0x1c
Node 0x26 [Vendor Defined Widget] wcaps 0xf00100: Mono
  Connection: 3
     0x14* 0x15 0x1c
--endcollapse--




!!ALSA Device nodes
!!-----------------


crw-rw---T+ 1 root audio 116,  7 Mar 24 08:57 /dev/snd/controlC0
crw-rw---T+ 1 root audio 116,  6 Mar 24 08:57 /dev/snd/hwC0D0
crw-rw---T+ 1 root audio 116,  5 Mar 24 08:57 /dev/snd/pcmC0D0c
crw-rw---T+ 1 root audio 116,  4 Mar 24 09:23 /dev/snd/pcmC0D0p
crw-rw---T+ 1 root audio 116,  3 Mar 24 08:57 /dev/snd/pcmC0D2c
crw-rw---T+ 1 root audio 116,  2 Mar 24 08:57 /dev/snd/pcmC0D2p
crw-rw---T+ 1 root audio 116,  1 Mar 24 08:57 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Mar 24 08:57 /dev/snd/timer


/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Mar 24 08:57 .
drwxr-xr-x 3 root root 220 Mar 24 08:57 ..
lrwxrwxrwx 1 root root  12 Mar 24 08:57 pci-0000:00:1b.0 -> ../controlC0




!!Aplay/Arecord output
!!--------------------


APLAY


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD1884 Analog [AD1884 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: AD1884 Alt Analog [AD1884 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ARECORD


**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD1884 Analog [AD1884 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: AD1884 Alt Analog [AD1884 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


!!Amixer output
!!-------------


!!-------Mixer controls for card 0 [Intel]


Card hw:0 'Intel'/'HDA Intel at 0xf01a0000 irq 45'
  Mixer name	: 'Analog Devices AD1884'
  Components	: 'HDA:11d41884,103c281e,00100100'
  Controls      : 34
  Simple ctrls  : 16
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 23
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Line Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 23
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 1 [33%] [10.00dB]
  Front Right: 1 [33%] [10.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 37 [69%] [-3.00dB] [on]
  Front Right: Capture 37 [69%] [-3.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 0 [0%] [-58.50dB] [off]
  Front Right: Capture 0 [0%] [-58.50dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Speaker Only' 'Line Out+Speaker'
  Item0: 'Line Out+Speaker'
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'




!!Alsactl output
!!--------------


--startcollapse--
state.Intel {
	control.1 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 39
		value.1 39
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 39'
			dbmin -5850
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.2 {
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
	control.3 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 39
		value.1 39
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 39'
			dbmin -5850
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.4 {
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
	control.5 {
		iface MIXER
		name 'Speaker Playback Volume'
		value 31
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 31'
			dbmin -4650
			dbmax 0
			dbvalue.0 0
		}
	}
	control.6 {
		iface MIXER
		name 'Speaker Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.7 {
		iface MIXER
		name 'Independent HP'
		value Disabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.8 {
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 23'
			dbmin -3450
			dbmax 0
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.9 {
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.10 {
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 23'
			dbmin -3450
			dbmax 0
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.11 {
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.12 {
		iface MIXER
		name 'Auto-Mute Mode'
		value 'Line Out+Speaker'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 'Speaker Only'
			item.2 'Line Out+Speaker'
		}
	}
	control.13 {
		iface MIXER
		name 'Input Source'
		value Mic
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Mic
			item.1 Line
		}
	}
	control.14 {
		iface MIXER
		name 'Input Source'
		index 1
		value Mic
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Mic
			item.1 Line
		}
	}
	control.15 {
		iface MIXER
		name 'Capture Volume'
		value.0 37
		value.1 37
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 54'
			dbmin -5850
			dbmax 2250
			dbvalue.0 -300
			dbvalue.1 -300
		}
	}
	control.16 {
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
	control.17 {
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 54'
			dbmin -5850
			dbmax 2250
			dbvalue.0 -5850
			dbvalue.1 -5850
		}
	}
	control.18 {
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.19 {
		iface MIXER
		name 'Mic Boost Volume'
		value.0 1
		value.1 1
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 1000
			dbvalue.1 1000
		}
	}
	control.20 {
		iface MIXER
		name 'Line Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.21 {
		iface MIXER
		name 'Master Playback Volume'
		value 39
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 39'
			dbmin -5850
			dbmax 0
			dbvalue.0 0
		}
	}
	control.22 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.23 {
		iface CARD
		name 'Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.24 {
		iface CARD
		name 'Line Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.25 {
		iface CARD
		name 'Line Out Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.26 {
		iface CARD
		name 'Front Headphone Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.27 {
		iface CARD
		name 'Speaker Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.28 {
		iface MIXER
		name 'Beep Playback Volume'
		value 15
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 15'
			dbmin -4500
			dbmax 0
			dbvalue.0 0
		}
	}
	control.29 {
		iface MIXER
		name 'Beep Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.30 {
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
	control.31 {
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
	control.32 {
		iface PCM
		device 2
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
	control.33 {
		iface PCM
		device 2
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
	control.34 {
		iface MIXER
		name 'Digital Capture Volume'
		value.0 60
		value.1 60
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 120'
			tlv '0000000100000008fffff44800000032'
			dbmin -3000
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
}
--endcollapse--




!!All Loaded Modules
!!------------------


Module
btrfs
raid6_pq
xor
ufs
qnx4
hfsplus
hfs
minix
ntfs
msdos
jfs
xfs
libcrc32c
reiserfs
bnep
rfcomm
bluetooth
usblp
snd_hda_codec_analog
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
i915
snd_seq_midi
joydev
snd_rawmidi
xpad
snd_seq_midi_event
snd_seq
usb_storage
ff_memless
snd_timer
snd_seq_device
drm_kms_helper
drm
gpio_ich
snd
psmouse
soundcore
mei_me
hp_wmi
snd_page_alloc
mei
i2c_algo_bit
coretemp
serio_raw
sparse_keymap
mac_hid
tpm_infineon
shpchp
ppdev
lpc_ich
video
wmi
parport_pc
lp
parport
floppy
e1000e
pata_acpi
ptp
pps_core




!!Sysfs Files
!!-----------


/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x02211030
0x12 0x01014010
0x13 0x99131150
0x14 0x02a11040
0x15 0x01813020
0x16 0x599311f0
0x1a 0x591321f0
0x1b 0x414511f0
0x1c 0x41a191f0


/sys/class/sound/hwC0D0/driver_pin_configs:


/sys/class/sound/hwC0D0/user_pin_configs:


/sys/class/sound/hwC0D0/init_verbs:


/sys/class/sound/hwC0D0/hints:




!!ALSA/HDA dmesg
!!--------------


[   10.582363] excessive driver sleep timeout (DSPL) 3875403759
[   10.582364] Modules linked in: i915(+) snd_seq_midi joydev snd_rawmidi xpad snd_seq_midi_event snd_seq usb_storage ff_memless snd_timer snd_seq_device drm_kms_helper drm gpio_ich snd psmouse soundcore mei_me hp_wmi snd_page_alloc mei i2c_algo_bit coretemp serio_raw sparse_keymap mac_hid tpm_infineon shpchp ppdev lpc_ich video wmi parport_pc lp parport floppy e1000e pata_acpi ptp pps_core
[   10.582393] CPU: 1 PID: 584 Comm: modprobe Not tainted 3.13.0-46-generic #79~precise1-Ubuntu
--
[   10.736165] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.061998] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   11.225197] scsi 4:0:0:0: Direct-Access     FNK TECH USB CARD READER  1.00 PQ: 0 ANSI: 0 CCS
--
[   11.583986]      Line=0x15
[   11.589657] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   11.589784] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.589886] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   11.589987] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.156620] usblp 3-2:1.0: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0033
```

---

### Post by Bucky Ball on 2015-03-24
@michael-piziak: In future, please put your code in [code] tags. I have added them in your last post. See the last link in my signature for how. Thanks.

---

### Post by Yellow Pasque on 2015-03-24
Well, Auto-Mute is enabled according to your info, but independent headphone volume is not, so maybe that's the issue.

```
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
```

If you fire up alsamixer and enable/toggle the 'Independent HP' option, do the speakers mute (and unmute) properly?
(To start alsamixer, just type it in terminal)
```
alsamixer
```

---

### Post by michael-piziak on 2015-03-24
I've toggled auto-mute mode and hp-independent mode.  The only thing that does occur is the internal speaker of the computer will mute when headphones are plugged in; however, sound still comes out of the speakers on the monitor (as the monitor has it's own audio wire that is plugged up in the rear of the computer - my headphone jack is on the front that I've been using).

By the way, is there a way to tell alsa mixer to restore its default settings, as I believe I've adjusted some things in there that shouldn't be adjusted.

---

### Post by Yellow Pasque on 2015-03-24
The Line Out is supposed to mute as well:
```
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Speaker Only' 'Line Out+Speaker'
  Item0: 'Line Out+Speaker'
```

I believe this will restore your settings:
```
sudo alsactl restore
```

---

### Post by michael-piziak on 2015-03-24
ok, the restore code worked great.

Now, the first 4 lines of code you had in that message - did you want me to type those into terminal ?

---

### Post by Yellow Pasque on 2015-03-24
No. With those 4 lines, I was just pointing out that it should be muting the line out (to the monitor). Unless I'm overlooking something (and it's very possible since this could be something affected by pulseaudio, which I don't use or know much about), I'd consider it a bug. If it was me, I would try a LiveUSB/CD of Ubuntu 15.04 to see if it exhibits the same behavior. If it works correctly in 15.04, it would be interesting to compare the alsa info from there.

---

### Post by michael-piziak on 2015-03-24
ok thanks.  I should have pointed out that I'm using 12.04 LTS.  Perhaps I will make a USB stick with 14.04 lts on it and boot and test it.  The reason why I stick with 12.04 LTS is mostly because my favorite emulator, Snes9x, just won't work with 14.04

Thanks for trying to help.  It's not that big of a deal to me that I'm overly concerned about it.

---

