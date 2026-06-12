---
title: "Headphones not working in Kubuntu 16.04"
date: 2016-07-17
forum: Hardware
---

### Post by aryakaran on 2016-07-17
I'm trying to set my new Kubuntu 16.04 system on a Alienware 15 R2 laptop. The speakers and usb headphones work properly but the headphone jack is not detected.

I have done some research about it and some people suggest to do some changes in the /etc/modprobe.d/alsa-base.conf configuration file.
I have tried to add the lines: 


options snd-hda-intel model=dell-alienware 
or
options snd-hda-intel model=dell-eq

but it did not change anything after rebooting. Also by executing alsamixer I have unmmuted all the options (however I did not see any option for headphone jack). Also I have installed pavucontrol but this software does not display any headphone jack option either.

Thanks for your help!

---

### Post by Yellow Pasque on 2016-07-17
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Is this one of the models with a Creative codec? I was hoping that Xenial (or more specifically, kernel 4.4) would solve the audio issues with Alienwares. I guess it's not that simple...
[https://github.com/torvalds/linux/commit/fe14f39e88c8ac16d0a051f8444a2294f8cb358c](https://github.com/torvalds/linux/commit/fe14f39e88c8ac16d0a051f8444a2294f8cb358c)

---

### Post by aryakaran on 2016-07-17
Hi, 

This is the output of the link you sent me. Yes it is a creative codec I think.

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Sun Jul 17 17:17:05 UTC 2016


!!Linux Distribution
!!------------------

Ubuntu 16.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 16.04 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/" UBUNTU_CODENAME=xenial


!!DMI Information
!!---------------

Manufacturer:      Alienware
Product Name:      Alienware 15 R2
Product Version:   1.2.14
Firmware Version:  1.2.14


!!Kernel Information
!!------------------

Kernel release:    4.4.0-31-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.4.0-31-generic
Library version:    1.1.0
Utilities version:  1.1.0


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

 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xdd128000 irq 145


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1f.3 0403: 8086:a170 (rev 31)
    Subsystem: 1028:0708


!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
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
snd_hda_intel: model=dell-alienware


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    model : dell-alienware,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : -1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Creative CA0132
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x11020011
Subsystem Id: 0x10280708
Revision Id: 0x100918
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 D3cold S3D3cold CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=1, wake=1
Node 0x02 [Audio Output] wcaps 0x49d: Stereo Amp-Out
  Device: name="CA0132 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e4]: 16000 44100 48000 88200 96000 192000
    bits [0x1f]: 8 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x49d: Stereo Amp-Out
  Amp-Out caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-Out vals:  [0x5a 0x5a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e4]: 16000 44100 48000 88200 96000 192000
    bits [0x1f]: 8 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x49d: Stereo Amp-Out
  Amp-Out caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-Out vals:  [0x5a 0x5a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e4]: 16000 44100 48000 88200 96000 192000
    bits [0x1f]: 8 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x691: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=16, device=0
  Control: name="IEC958 Playback Pro Mask", index=16, device=0
  Control: name="IEC958 Playback Default", index=16, device=0
  Control: name="IEC958 Playback Switch", index=16, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="CA0132 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x691: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Audio Input] wcaps 0x100591: Stereo
  Device: name="CA0132 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x1e4]: 16000 44100 48000 88200 96000
    bits [0x1f]: 8 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x08 [Audio Input] wcaps 0x10059b: Stereo Amp-In
  Control: name="Analog-Mic2 Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Analog-Mic2 Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="CA0132 Analog Mic-In2", type="Audio", device=2
  Amp-In caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-In vals:  [0x5a 0x5a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x1e4]: 16000 44100 48000 88200 96000
    bits [0x1f]: 8 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x11
Node 0x09 [Audio Input] wcaps 0x100791: Stereo Digital
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Device: name="CA0132 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x1f0]: 32000 44100 48000 88200 96000
    bits [0x1a]: 16 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x0a [Audio Input] wcaps 0x10079b: Stereo Digital Amp-In
  Control: name="What U Hear Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="What U Hear Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="CA0132 What U Hear", type="Audio", device=4
  Amp-In caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-In vals:  [0x5a 0x5a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x1ec]: 16000 22050 44100 48000 88200 96000
    bits [0x1b]: 8 16 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x13
Node 0x0b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
Node 0x0c [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x014580f0: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Purple
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x05
Node 0x0d [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x014570f0: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Yellow
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x0e [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000020: IN
  Pin Default 0x01c530f0: [Jack] SPDIF In at Ext Rear
    Conn = Optical, Color = Blue
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x0f [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
Node 0x10 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x02216011: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x03
Node 0x11 [Pin Complex] wcaps 0x40058b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000134: IN OUT Detect
    Vref caps: HIZ
  Pin Default 0x02012014: [Jack] Line Out at Ext Front
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x04
Node 0x12 [Pin Complex] wcaps 0x400481: Stereo
  Control: name="Mic1-Boost (30dB) Capture Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=0, ofs=0
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x37a791f0: [Jack] Mic at Oth Mobile-In
    Conn = Analog, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000020: IN
  Pin Default 0x908700f0: [Fixed] Line In at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x14 [Beep Generator Widget] wcaps 0x70040c: Mono Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1c]
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x15 [Vendor Defined Widget] wcaps 0xf00600: Mono Digital
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x16 [Vendor Defined Widget] wcaps 0xf00680: Mono Digital
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x17 [Audio Output] wcaps 0x49d: Stereo Amp-Out
  Amp-Out caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-Out vals:  [0x5a 0x5a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5ec]: 16000 22050 44100 48000 88200 96000 192000
    bits [0x1f]: 8 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x18 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x500000f0: [N/A] Line Out at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x17
Codec: Intel Skylake HDMI
Address: 2
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x80862809
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Control: name="ELD", index=0, device=7
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x07 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Control: name="ELD", index=0, device=8
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  2 Jul 17 12:29 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 12 Jul 17 12:29 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116, 13 Jul 17 12:29 /dev/snd/hwC1D2
crw-rw----+ 1 root audio 116,  4 Jul 17 12:30 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  3 Jul 17 18:15 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  8 Jul 17 18:15 /dev/snd/pcmC1D1c
crw-rw----+ 1 root audio 116,  7 Jul 17 12:30 /dev/snd/pcmC1D1p
crw-rw----+ 1 root audio 116,  5 Jul 17 12:29 /dev/snd/pcmC1D2c
crw-rw----+ 1 root audio 116,  9 Jul 17 12:30 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116,  6 Jul 17 12:29 /dev/snd/pcmC1D4c
crw-rw----+ 1 root audio 116, 10 Jul 17 12:30 /dev/snd/pcmC1D7p
crw-rw----+ 1 root audio 116, 11 Jul 17 12:30 /dev/snd/pcmC1D8p
crw-rw----+ 1 root audio 116,  1 Jul 17 12:29 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jul 17 12:29 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jul 17 12:29 .
drwxr-xr-x 3 root root 340 Jul 17 12:29 ..
lrwxrwxrwx 1 root root  12 Jul 17 12:29 pci-0000:00:1f.3 -> ../controlC1


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 2: CA0132 Analog Mic-In2 [CA0132 Analog Mic-In2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 4: CA0132 What U Hear [CA0132 What U Hear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 1 [PCH]

Card hw:1 'PCH'/'HDA Intel PCH at 0xdd128000 irq 145'
  Mixer name    : 'Creative CA0132'
  Components    : 'HDA:11020011,10280708,00100918 HDA:80862809,80860101,00100000'
  Controls      : 64
  Simple ctrls  : 28
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 99
  Mono:
  Front Left: Playback 60 [61%] [-30.00dB] [on]
  Front Right: Playback 60 [61%] [-30.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic SVM',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Mic1-Boost (30dB)',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',16
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 99
  Front Left: Capture 99 [100%] [9.00dB] [on]
  Front Right: Capture 99 [100%] [9.00dB] [on]
Simple mixer control 'AMic1/DMic',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'AMic1/DMic Auto Detect',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Analog-Mic2',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 99
  Front Left: Capture 90 [91%] [0.00dB] [on]
  Front Right: Capture 90 [91%] [0.00dB] [on]
Simple mixer control 'CrystalVoice',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Crystalizer',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Dialog Plus',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Echo Cancellation',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Equalizer',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Noise Reduction',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'PlayEnhancement',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Smart Volume',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Voice Focus',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'VoiceFX',0
  Capabilities: cenum
  Items: 'Neutral' 'Female2Male' 'Male2Female' 'ScrappyKid' 'Elderly' 'Orc' 'Elf' 'Dwarf' 'AlienBrute' 'Robot' 'Marine' 'Emo' 'DeepVoice' 'Munchkin'
  Item0: 'Neutral'
Simple mixer control 'What U Hear',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 99
  Front Left: Capture 90 [91%] [0.00dB] [on]
  Front Right: Capture 90 [91%] [0.00dB] [on]
Simple mixer control 'X-Bass',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.PCH {
    control.1 {
        iface MIXER
        name 'Master Playback Volume'
        value.0 60
        value.1 60
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 99'
            dbmin -9000
            dbmax 900
            dbvalue.0 -3000
            dbvalue.1 -3000
        }
    }
    control.2 {
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
    control.3 {
        iface MIXER
        name 'Capture Volume'
        value.0 99
        value.1 99
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 99'
            dbmin -9000
            dbmax 900
            dbvalue.0 900
            dbvalue.1 900
        }
    }
    control.4 {
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
    control.5 {
        iface MIXER
        name 'Analog-Mic2 Capture Volume'
        value.0 90
        value.1 90
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 99'
            dbmin -9000
            dbmax 900
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.6 {
        iface MIXER
        name 'Analog-Mic2 Capture Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.7 {
        iface MIXER
        name 'What U Hear Capture Volume'
        value.0 90
        value.1 90
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 99'
            dbmin -9000
            dbmax 900
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.8 {
        iface MIXER
        name 'What U Hear Capture Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.9 {
        iface MIXER
        name 'Mic1-Boost (30dB) Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.10 {
        iface MIXER
        name 'HP/Speaker Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.11 {
        iface MIXER
        name 'AMic1/DMic Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.12 {
        iface MIXER
        name 'HP/Speaker Auto Detect Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.13 {
        iface MIXER
        name 'AMic1/DMic Auto Detect Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.14 {
        iface MIXER
        name 'Surround Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.15 {
        iface MIXER
        name 'Crystalizer Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.16 {
        iface MIXER
        name 'Dialog Plus Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.17 {
        iface MIXER
        name 'Smart Volume Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.18 {
        iface MIXER
        name 'X-Bass Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.19 {
        iface MIXER
        name 'Equalizer Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.20 {
        iface MIXER
        name 'Echo Cancellation Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.21 {
        iface MIXER
        name 'Voice Focus Capture Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.22 {
        iface MIXER
        name 'Mic SVM Capture Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.23 {
        iface MIXER
        name 'Noise Reduction Capture Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.24 {
        iface MIXER
        name 'PlayEnhancement Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.25 {
        iface MIXER
        name 'CrystalVoice Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.26 {
        iface MIXER
        name 'VoiceFX Capture Switch'
        value Neutral
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Neutral
            item.1 Female2Male
            item.2 Male2Female
            item.3 ScrappyKid
            item.4 Elderly
            item.5 Orc
            item.6 Elf
            item.7 Dwarf
            item.8 AlienBrute
            item.9 Robot
            item.10 Marine
            item.11 Emo
            item.12 DeepVoice
            item.13 Munchkin
        }
    }
    control.27 {
        iface CARD
        name 'Mic Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.28 {
        iface CARD
        name 'Front Line Out Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.29 {
        iface CARD
        name 'Line Out Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.30 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 16
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.31 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 16
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.32 {
        iface MIXER
        name 'IEC958 Playback Default'
        index 16
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.33 {
        iface MIXER
        name 'IEC958 Playback Switch'
        index 16
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.34 {
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.35 {
        iface MIXER
        name 'IEC958 Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.36 {
        iface MIXER
        name 'IEC958 Capture Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.37 {
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
    control.38 {
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
    control.39 {
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
    control.40 {
        iface PCM
        device 4
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
        device 1
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
    control.42 {
        iface PCM
        device 1
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
    control.43 {
        iface CARD
        name 'HDMI/DP,pcm=3 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.44 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.45 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.46 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.47 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.48 {
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
    control.49 {
        iface CARD
        name 'HDMI/DP,pcm=7 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.50 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 1
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.51 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 1
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.52 {
        iface MIXER
        name 'IEC958 Playback Default'
        index 1
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.53 {
        iface MIXER
        name 'IEC958 Playback Switch'
        index 1
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.54 {
        iface PCM
        device 7
        name ELD
        value ''
        comment {
            access 'read volatile'
            type BYTES
            count 0
        }
    }
    control.55 {
        iface CARD
        name 'HDMI/DP,pcm=8 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.56 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 2
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.57 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 2
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.58 {
        iface MIXER
        name 'IEC958 Playback Default'
        index 2
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.59 {
        iface MIXER
        name 'IEC958 Playback Switch'
        index 2
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.60 {
        iface PCM
        device 8
        name ELD
        value ''
        comment {
            access 'read volatile'
            type BYTES
            count 0
        }
    }
    control.61 {
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
    control.62 {
        iface PCM
        device 7
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
    control.63 {
        iface PCM
        device 8
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
    control.64 {
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
rfcomm
arc4
snd_hda_codec_hdmi
bnep
dell_wmi
snd_hda_codec_ca0132
sparse_keymap
intel_rapl
x86_pkg_temp_thermal
intel_powerclamp
coretemp
kvm_intel
snd_hda_intel
kvm
snd_hda_codec
snd_hda_core
irqbypass
snd_hwdep
crct10dif_pclmul
crc32_pclmul
uvcvideo
videobuf2_vmalloc
aesni_intel
videobuf2_memops
videobuf2_v4l2
ath10k_pci
aes_x86_64
lrw
videobuf2_core
ath10k_core
gf128mul
v4l2_common
glue_helper
snd_pcm
ablk_helper
ath
videodev
cryptd
mac80211
joydev
input_leds
snd_seq_midi
snd_seq_midi_event
serio_raw
snd_rawmidi
media
cfg80211
snd_seq
rtsx_pci_ms
memstick
snd_seq_device
snd_timer
btusb
btrtl
snd
mei_me
soundcore
shpchp
processor_thermal_device
mei
hci_uart
intel_soc_dts_iosf
intel_lpss_acpi
btbcm
intel_lpss
btqca
int3403_thermal
btintel
int340x_thermal_zone
mac_hid
bluetooth
tpm_crb
acpi_als
dell_rbtn
int3400_thermal
kfifo_buf
acpi_thermal_rel
acpi_pad
industrialio
ip6t_REJECT
nf_reject_ipv6
nf_log_ipv6
xt_hl
ip6t_rt
nf_conntrack_ipv6
nf_defrag_ipv6
ipt_REJECT
nf_reject_ipv4
nf_log_ipv4
nf_log_common
xt_LOG
xt_limit
xt_tcpudp
xt_addrtype
nf_conntrack_ipv4
nf_defrag_ipv4
xt_conntrack
ip6table_filter
ip6_tables
nf_conntrack_netbios_ns
nf_conntrack_broadcast
nf_nat_ftp
nf_nat
nf_conntrack_ftp
nf_conntrack
iptable_filter
parport_pc
ip_tables
x_tables
ppdev
lp
parport
autofs4
hid_generic
usbhid
rtsx_pci_sdmmc
nouveau
i915_bpo
mxm_wmi
intel_ips
ttm
i2c_algo_bit
drm_kms_helper
syscopyarea
psmouse
sysfillrect
sysimgblt
fb_sys_fops
nvme
ahci
alx
rtsx_pci
drm
libahci
mdio
wmi
video
pinctrl_sunrisepoint
i2c_hid
pinctrl_intel
hid
fjes


!!Sysfs Files
!!-----------

/sys/class/sound/hwC1D0/init_pin_configs:
0x0b 0x01014010
0x0c 0x014580f0
0x0d 0x014570f0
0x0e 0x01c530f0
0x0f 0x0221401f
0x10 0x02216011
0x11 0x02012014
0x12 0x37a791f0
0x13 0x908700f0
0x18 0x500000f0

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D0/hints:

/sys/class/sound/hwC1D2/init_pin_configs:
0x05 0x18560010
0x06 0x18560010
0x07 0x18560010

/sys/class/sound/hwC1D2/driver_pin_configs:

/sys/class/sound/hwC1D2/user_pin_configs:

/sys/class/sound/hwC1D2/init_verbs:

/sys/class/sound/hwC1D2/hints:


!!ALSA/HDA dmesg
!!--------------

[    3.282201] USB Video Class driver (1.1.1)
[    3.295503] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915_bpo])
[    3.320715] EXT4-fs (nvme0n1p6): mounted filesystem with ordered data mode. Opts: (null)
--
[    3.338664] intel_rapl: Found RAPL domain dram
[    3.339637] snd_hda_codec_ca0132 hdaudioC1D0: autoconfig for CA0132: line_outs=1 (0xb/0x0/0x0/0x0/0x0) type:speaker
[    3.339641] snd_hda_codec_ca0132 hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.339643] snd_hda_codec_ca0132 hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.339644] snd_hda_codec_ca0132 hdaudioC1D0:    mono: mono_out=0x0
[    3.339646] snd_hda_codec_ca0132 hdaudioC1D0:    inputs:
[    3.339647] snd_hda_codec_ca0132 hdaudioC1D0:      Mic=0x12
[    3.339649] snd_hda_codec_ca0132 hdaudioC1D0:      Line=0x11
[    3.340652] input: Dell WMI hotkeys as /devices/virtual/input/input9
--
[    3.673999] IPv6: ADDRCONF(NETDEV_UP): enp59s0: link is not ready
[    3.901852] snd_hda_codec_ca0132 hdaudioC1D0: ca0132 DSP downloaded and running
[    4.132118] input: HDA Intel PCH Front Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card1/input10
[    4.132167] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card1/input11
[    4.132217] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card1/input12
[    4.132273] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card1/input13
[    4.132324] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card1/input14
[    4.761690] snd_hda_codec_ca0132 hdaudioC1D0: ca0132 DSP downloaded and running
[    5.686844] ath10k_pci 0000:3c:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 2 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
```

---

### Post by Yellow Pasque on 2016-07-17
Yeah, it doesn't look it's seeing a headphone jack (hp_outs=0). Note that you left the "model=dell-alienware" hack in place. If it doesn't help, remove it.
```
[    3.339637] snd_hda_codec_ca0132 hdaudioC1D0: autoconfig for CA0132: line_outs=1 (0xb/0x0/0x0/0x0/0x0) type:speaker
[    3.339641] snd_hda_codec_ca0132 hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.339643] snd_hda_codec_ca0132 hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.339644] snd_hda_codec_ca0132 hdaudioC1D0:    mono: mono_out=0x0
[    3.339646] snd_hda_codec_ca0132 hdaudioC1D0:    inputs:
[    3.339647] snd_hda_codec_ca0132 hdaudioC1D0:      Mic=0x12
[    3.339649] snd_hda_codec_ca0132 hdaudioC1D0:      Line=0x11
```

---

### Post by aryakaran on 2016-07-17
Ok, removed.
Do you think there is anything I can do to be able to use the headphone jack?

Thanks for your help!

---

### Post by Jack Harper on 2016-07-17
I have a very very similar problem on my Asus Rog and I "solved" it by plugging my headphones into line out, it works for now though it is not a real solution.

---

### Post by aryakaran on 2016-07-19
Thanks for the suggestion. Unfortunately my laptop does not have line out jack.

---

### Post by msknight on 2016-07-20
I've used USB soundcards in the past. I have two of the Startech ICUSBAUDIOB which aren't too expensive and get me around issues while waiting for a fix. Not the most elegant of solutions, but it worked for me.

---

### Post by msknight on 2016-07-20
If money isn't too much of an object and you want better quality, I use a Centrance DacPort Slim for laptops where I get motherboard interferance, which sometimes tends to happen with the ones that try to pack too much tech in to an ultra thin case. I also use the DacPort Slim for my Beyerdynamic and Sennheiser headphones, which are 250 and 300 ohm respectively... because the Startech will only handle around 60 ohm cans.

The DacPort Slim, if kicked in to high gain mode and ramped all the way to max volume (according to the manufacturer in a conversation on MassDrop) will also put out enough juice to act as a Line Out as well.

---

### Post by Yellow Pasque on 2016-07-20
I was wondering if you tried manipulating these settings in alsamixer:
```
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
```

Other than that, maybe try playing with hdajackretask:
```
sudo apt-get install alsa-tools-gui
hdajackretask
```

I'm guessing 0x0f is your headphone/headset jack (not sure though).
```
Node 0x0f [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
```

---

### Post by aryakaran on 2016-07-21
Hi Thanks for the suggestions.

When I try to use hdajackretask I loose sound even through the speakers and the Kubuntu menu bar disappears :(

---

