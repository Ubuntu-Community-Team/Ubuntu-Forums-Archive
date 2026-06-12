---
title: "Alsa headphone recognized as surround speakers"
date: 2013-08-27
forum: Hardware
---

### Post by Jonathan_Birk on 2013-08-27
Hi,

currently I'm setting up a lubuntu on an old Fujitsu Lifebook S7110 but now got stuck with the Sound
My problems are:
[LIST=1]
[*]The headphone jack is setup as surround speakers (in alsamixer) 
[*]Whenever I mute one of Master, PCM, Front or Surround all four get muted and i have to unmute all 4 seperately again to hear something again. 
[/LIST]

Output of alsa-info.sh:
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.62
!!################################

!!Script ran on: Tue Aug 27 13:51:16 UTC 2013


!!Linux Distribution
!!------------------

Ubuntu 13.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 13.04" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 13.04" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      FUJITSU SIEMENS
Product Name:      LIFEBOOK S7110
Product Version:    
Firmware Version:  Version 1.12 


!!Kernel Information
!!------------------

Kernel release:    3.8.0-29-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.8.0-29-generic
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

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0640000 irq 45


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
    Subsystem: 10cf:1397


!!Modprobe options (Sound related)
!!--------------------------------

snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_hda_intel: model=fujitsu


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
    model : fujitsu,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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

Codec: Realtek ALC262
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0262
Subsystem Id: 0x10cf0000
Revision Id: 0x100002
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC262 Analog", type="Audio", device=0
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC262 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=4, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC262 Analog", type="Audio", device=2
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=2, device=0
  Control: name="Capture Volume", index=2, device=0
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80]
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
  IEC Coding Type: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Dock Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Dock Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Internal Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Internal Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="CD Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="CD Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x1f 0x1f] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1c 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x1f 0x1f]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x80]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x01]
  Connection: 2
     0x02 0x0b
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Surround Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x032110f0: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 2
     0x0c 0x0d*
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Front Phantom Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0xb7231110: [Fixed] HP Out at Oth Mobile-In
    Conn = ATAPI, Color = Black
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x03a118f0: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c* 0x0d
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Internal Mic Phantom Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x03 0x03]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0xb7a311f0: [Fixed] Mic at Oth Mobile-In
    Conn = ATAPI, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Dock Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Dock Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x23a11020: [Jack] Mic at Sep Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=05, enabled=1
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Dock Headphone Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x2321101f: [Jack] HP Out at Sep Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=01, enabled=1
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Control: name="CD Phantom Jack", index=0, device=0
  Pincap 0x00000020: IN
  Pin Default 0x88331121: [Fixed] CD at Ext Drive Bar
    Conn = ATAPI, Color = Black
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0xb793112f: [Fixed] Aux at Oth Mobile-In
    Conn = ATAPI, Color = Black
    DefAssociation = 0x2, Sequence = 0xf
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400280: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono
  Volume-Knob: delta=0, steps=32, direct=0, val=64
  Unsolicited: tag=00, enabled=0
  Connection: 0
Node 0x22 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=2, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Codec: LSI ID 1040
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x11c11040
Subsystem Id: 0x11c10001
Revision Id: 0x100200
Modem Function Group: 0x1
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  7 Aug 27 15:21 /dev/snd/controlC0
crw-rw---T+ 1 root audio 116,  6 Aug 27 15:21 /dev/snd/hwC0D0
crw-rw---T+ 1 root audio 116,  5 Aug 27 15:21 /dev/snd/hwC0D1
crw-rw---T+ 1 root audio 116,  4 Aug 27 15:22 /dev/snd/pcmC0D0c
crw-rw---T+ 1 root audio 116,  3 Aug 27 15:35 /dev/snd/pcmC0D0p
crw-rw---T+ 1 root audio 116,  2 Aug 27 15:21 /dev/snd/pcmC0D2c
crw-rw---T+ 1 root audio 116,  1 Aug 27 15:21 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Aug 27 15:21 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Aug 27 15:21 .
drwxr-xr-x 3 root root 220 Aug 27 15:21 ..
lrwxrwxrwx 1 root root  12 Aug 27 15:21 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC262 Analog [ALC262 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xf0640000 irq 45'
  Mixer name    : 'Realtek ALC262'
  Components    : 'HDA:10ec0262,10cf0000,00100002 HDA:11c11040,11c10001,00100200'
  Controls      : 42
  Simple ctrls  : 20
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [22.50dB] [off]
  Front Right: Capture 23 [74%] [22.50dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-12.00dB] [off]
  Front Right: Capture 0 [0%] [-12.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-12.00dB] [off]
  Front Right: Capture 0 [0%] [-12.00dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Dock Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Dock Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Dock Mic' 'Internal Mic' 'CD'
  Item0: 'Internal Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Dock Mic' 'Internal Mic' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Dock Mic' 'Internal Mic' 'CD'
  Item0: 'Mic'
Simple mixer control 'Internal Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]


!!Alsactl output
!!--------------

--startcollapse--
state.Intel {
    control.1 {
        iface MIXER
        name 'Front Playback Volume'
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
    control.2 {
        iface MIXER
        name 'Front Playback Switch'
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
        name 'Surround Playback Volume'
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
    control.4 {
        iface MIXER
        name 'Surround Playback Switch'
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
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.6 {
        iface MIXER
        name 'Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.7 {
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
    control.8 {
        iface MIXER
        name 'Dock Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.9 {
        iface MIXER
        name 'Dock Mic Playback Switch'
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
        name 'Internal Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.11 {
        iface MIXER
        name 'Internal Mic Playback Switch'
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
        name 'CD Playback Volume'
        value.0 31
        value.1 31
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 1200
            dbvalue.1 1200
        }
    }
    control.13 {
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
    control.14 {
        iface MIXER
        name 'Auto-Mute Mode'
        value Enabled
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Disabled
            item.1 Enabled
        }
    }
    control.15 {
        iface MIXER
        name 'Mic Boost Volume'
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
    control.16 {
        iface MIXER
        name 'Dock Mic Boost Volume'
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
    control.17 {
        iface MIXER
        name 'Internal Mic Boost Volume'
        value.0 3
        value.1 3
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3000
            dbvalue.0 3000
            dbvalue.1 3000
        }
    }
    control.18 {
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
    control.19 {
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
    control.20 {
        iface MIXER
        name 'Capture Switch'
        index 2
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.21 {
        iface MIXER
        name 'Capture Volume'
        value.0 23
        value.1 23
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -1200
            dbmax 3450
            dbvalue.0 2250
            dbvalue.1 2250
        }
    }
    control.22 {
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -1200
            dbmax 3450
            dbvalue.0 -1200
            dbvalue.1 -1200
        }
    }
    control.23 {
        iface MIXER
        name 'Capture Volume'
        index 2
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -1200
            dbmax 3450
            dbvalue.0 -1200
            dbvalue.1 -1200
        }
    }
    control.24 {
        iface MIXER
        name 'Input Source'
        value 'Internal Mic'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mic
            item.1 'Dock Mic'
            item.2 'Internal Mic'
            item.3 CD
        }
    }
    control.25 {
        iface MIXER
        name 'Input Source'
        index 1
        value Mic
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mic
            item.1 'Dock Mic'
            item.2 'Internal Mic'
            item.3 CD
        }
    }
    control.26 {
        iface MIXER
        name 'Input Source'
        index 2
        value Mic
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mic
            item.1 'Dock Mic'
            item.2 'Internal Mic'
            item.3 CD
        }
    }
    control.27 {
        iface MIXER
        name 'Beep Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.28 {
        iface MIXER
        name 'Beep Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.29 {
        iface MIXER
        name 'Master Playback Volume'
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
    control.30 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.31 {
        iface CARD
        name 'Headphone Front Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.32 {
        iface CARD
        name 'Headphone Surround Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.33 {
        iface CARD
        name 'Dock Headphone Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.34 {
        iface CARD
        name 'Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.35 {
        iface CARD
        name 'Dock Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.36 {
        iface CARD
        name 'Internal Mic Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.37 {
        iface CARD
        name 'CD Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.38 {
        iface PCM
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        value.2 0
        value.3 0
        comment {
            access read
            type INTEGER
            count 4
            range '0 - 36'
        }
    }
    control.39 {
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
    control.40 {
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
    control.41 {
        iface PCM
        device 2
        name 'Capture Channel Map'
        index 1
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.42 {
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
dm_crypt
snd_atiixp_modem
snd_via82xx_modem
snd_intel8x0m
snd_ac97_codec
ac97_bus
coretemp
bnep
kvm
rfcomm
joydev
bluetooth
ppdev
snd_hda_codec_realtek
snd_hda_intel
wl
snd_hda_codec
snd_hwdep
snd_pcm
lib80211
snd_page_alloc
arc4
pcmcia
snd_seq_midi
microcode
snd_seq_midi_event
iwl3945
iwlegacy
snd_rawmidi
irda
crc_ccitt
yenta_socket
snd_seq
mac80211
snd_seq_device
pcmcia_rsrc
parport_pc
snd_timer
fujitsu_laptop
pcmcia_core
mac_hid
lpc_ich
snd
cfg80211
psmouse
serio_raw
soundcore
lp
parport
i915
i2c_algo_bit
drm_kms_helper
firewire_ohci
firewire_core
drm
sky2
crc_itu_t
video


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x14 0x032110f0
0x15 0xb7231110
0x16 0x411111f0
0x18 0x03a118f0
0x19 0xb7a311f0
0x1a 0x23a11020
0x1b 0x2321101f
0x1c 0x88331121
0x1d 0xb793112f
0x1e 0x411111f0
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:

/sys/class/sound/hwC0D1/init_pin_configs:

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:

/sys/class/sound/hwC0D1/hints:


!!ALSA/HDA dmesg
!!--------------

[   24.803748] wl: module license 'MIXED/Proprietary' taints kernel.
[   25.229325] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   25.753252] Bluetooth: Core ver 2.16
--
[   25.850606] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   25.993469] input: HDA Intel Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   25.993760] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   25.996123] input: HDA Intel Dock Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   25.997101] input: HDA Intel Headphone Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   25.998425] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

```

---

### Post by digerydoo on 2013-09-22
i've got the same problem and with the same laptop (fujitsu S7110), but as i've recognised the 'headphon' and 'front' have swapped places. i've also tried to find a way to make my distro (ubuntu 12.04 server+LXDE) to automute while headphones plugged in, which depends on 'alsa' as well, but no solution found so far. i just kept on usin' it as is .

---

