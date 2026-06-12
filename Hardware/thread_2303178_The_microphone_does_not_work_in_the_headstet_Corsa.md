---
title: "The microphone does not work in the headstet Corsair Raptor HS30 on Ubuntu 15.10"
date: 2015-11-16
forum: Hardware
---

### Post by mateo14 on 2015-11-16
Hi

In the last week, I bought Corsair Raptor HS30, which works with the Mac but  I have some issues with this device on Ubuntu. 

The sound is working, and I can use headphones without the problem.  Unfortunately, I noticed that the microphone does not work on Ubuntu  14.04, 15.04, and 15.10. I tried to change settings in alsa-mixer,  pavucontrol etc. I tried to add some options that I found on the  internet into the configuration file alsa-base.conf.

Unfortunately, I do not have too many ideas how to activate the microphone in Ubuntu. Can you help me?

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Tue Nov 17 02:24:42 UTC 2015


!!Linux Distribution
!!------------------

Ubuntu 15.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 15.10"  NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 15.10"  HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/"  BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      Apple Inc.
Product Name:      Macmini4,1
Product Version:   1.0
Firmware Version:      MM41.88Z.0042.B03.1111072100


!!Kernel Information
!!------------------

Kernel release:    4.2.0-18-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.2.0-18-generic
Library version:    1.0.29
Utilities version:  1.0.29


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

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd3580000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

00:08.0 Audio device: NVIDIA Corporation MCP89 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:08.0 0403: 10de:0d94 (rev a2)
	Subsystem: 10de:cb89


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
snd_hda_intel: model=auto


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(n    ull),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(nul   l),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model :  auto,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(nul    l),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)   ,(null),(null),(null)
	patch :  (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(n    ull),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(nul   l),(null),(null),(null)
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

Codec: Cirrus Logic CS4206
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10134206
Subsystem Id: 0x106b0300
Revision Id: 0x100301
No Modem Function Group found
Default PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=4, o=0, i=0, unsolicited=0, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=1, dir=1, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0xd041d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x73, nsteps=0x7f, stepsize=0x01, mute=1
  Amp-Out vals:  [0x5b 0x5b]
  Converter: stream=5, channel=0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x03 [Audio Output] wcaps 0xd041d: Stereo Amp-Out
  Control: name="Bass Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Bass Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x73, nsteps=0x7f, stepsize=0x01, mute=1
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=5, channel=0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x04 [Audio Output] wcaps 0xd041d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CS4206 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x73, nsteps=0x7f, stepsize=0x01, mute=1
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=5, channel=0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x05 [Audio Input] wcaps 0x18051b: Stereo Amp-In
  Amp-In caps: ofs=0x33, nsteps=0x3f, stepsize=0x03, mute=1
  Amp-In vals:  [0xb3 0xb3]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x1f5]: 8000 16000 32000 44100 48000 88200 96000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 8 samples
  Connection: 2
     0x0c* 0x12
Node 0x06 [Audio Input] wcaps 0x18051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="CS4206 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x33, nsteps=0x3f, stepsize=0x03, mute=1
  Amp-In vals:  [0x3f 0x3f]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x1f5]: 8000 16000 32000 44100 48000 88200 96000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 8 samples
  Connection: 2
     0x0d* 0x0e
Node 0x07 [Audio Input] wcaps 0x180791: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital: Preemphasis Non-Copyright
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x570]: 32000 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x7]: PCM FLOAT AC3
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 8 samples
  Connection: 1
     0x0f
Node 0x08 [Audio Output] wcaps 0x40611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=16, device=0
  Control: name="IEC958 Playback Pro Mask", index=16, device=0
  Control: name="IEC958 Playback Default", index=16, device=0
  Control: name="IEC958 Playback Switch", index=16, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="CS4206 Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x7]: PCM FLOAT AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x09 [Pin Complex] wcaps 0x410581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x012b4040: [Jack] HP Out at Ext Rear
    Conn = Comb, Color = Green
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 1 samples
  Connection: 1
     0x02
Node 0x0a [Pin Complex] wcaps 0x410581: Stereo
  Pincap 0x00000054: OUT Detect Balanced
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 1 samples
  Connection: 1
     0x03
Node 0x0b [Pin Complex] wcaps 0x410101: Stereo
  Pincap 0x00000050: OUT Balanced
  Pin Default 0x90100130: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Delay: 1 samples
  Connection: 1
     0x04
Node 0x0c [Pin Complex] wcaps 0x41048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000024: IN Detect
  Pin Default 0x018b3010: [Jack] Line In at Ext Rear
    Conn = Comb, Color = Blue
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 1 samples
Node 0x0d [Pin Complex] wcaps 0x41048b: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x03 0x03]
  Pincap 0x00001764: IN Detect Balanced
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 1 samples
Node 0x0e [Pin Complex] wcaps 0x41000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Delay: 1 samples
Node 0x0f [Pin Complex] wcaps 0x410681: Stereo Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x01cbe020: [Jack] SPDIF In at Ext Rear
    Conn = Comb, Color = White
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 1 samples
Node 0x10 [Pin Complex] wcaps 0x410301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x014be050: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = White
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Delay: 1 samples
  Connection: 1
     0x08
Node 0x11 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=22
Node 0x12 [Pin Complex] wcaps 0x41000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Delay: 1 samples
Node 0x13 [Beep Generator Widget] wcaps 0x700000: Mono
Node 0x14 [Audio Output] wcaps 0x40611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x7]: PCM FLOAT AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x15 [Pin Complex] wcaps 0x410301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Delay: 1 samples
  Connection: 1
     0x14
Codec: Nvidia MCP89 HDMI
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de000c
Subsystem Id: 0x10de0101
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x04
Codec: Nvidia MCP89 HDMI
Address: 4
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de000c
Subsystem Id: 0x10de0101
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Control: name="ELD", index=0, device=7
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x04
Codec: Nvidia MCP89 HDMI
Address: 5
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de000c
Subsystem Id: 0x10de0101
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Control: name="ELD", index=0, device=8
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x04
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  2 Nov 17 01:55 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  9 Nov 17 01:55 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 10 Nov 17 01:55 /dev/snd/hwC0D3
crw-rw----+ 1 root audio 116, 11 Nov 17 01:55 /dev/snd/hwC0D4
crw-rw----+ 1 root audio 116, 12 Nov 17 01:55 /dev/snd/hwC0D5
crw-rw----+ 1 root audio 116,  4 Nov 17 02:03 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  3 Nov 17 02:22 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  5 Nov 17 02:03 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  6 Nov 17 02:03 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  7 Nov 17 02:03 /dev/snd/pcmC0D7p
crw-rw----+ 1 root audio 116,  8 Nov 17 02:03 /dev/snd/pcmC0D8p
crw-rw----+ 1 root audio 116,  1 Nov 17 02:03 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Nov 17 01:55 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Nov 17 01:55 .
drwxr-xr-x 3 root root 320 Nov 17 01:55 ..
lrwxrwxrwx 1 root root  12 Nov 17 01:55 pci-0000:00:08.0 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CS4206 Analog [CS4206 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: CS4206 Digital [CS4206 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CS4206 Analog [CS4206 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [NVidia]

Card hw:0 'NVidia'/'HDA NVidia at 0xd3580000 irq 22'
  Mixer name	: 'Nvidia MCP89 HDMI'
  Components	: 'HDA:10134206,106b0300,00100301 HDA:10de000c,10de0101,00100200'
  Controls      : 48
  Simple ctrls  : 14
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 103 [81%] [-12.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 115 [91%] [0.00dB] [on]
  Front Right: Playback 115 [91%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 0 [0%] [-57.50dB] [off]
  Front Right: Playback 0 [0%] [-57.50dB] [off]
Simple mixer control 'Bass Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 0 [0%] [-57.50dB] [off]
  Front Right: Playback 0 [0%] [-57.50dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
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
  Limits: Capture 0 - 63
  Front Left: Capture 63 [100%] [12.00dB] [on]
  Front Right: Capture 63 [100%] [12.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]


!!Alsactl output
!!--------------

--startcollapse--
state.NVidia {
	control.1 {
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 127'
			dbmin -5750
			dbmax 600
			dbvalue.0 -5750
			dbvalue.1 -5750
		}
	}
	control.2 {
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Bass Speaker Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 127'
			dbmin -5750
			dbmax 600
			dbvalue.0 -5750
			dbvalue.1 -5750
		}
	}
	control.4 {
		iface MIXER
		name 'Bass Speaker Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 115
		value.1 115
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 127'
			dbmin -5750
			dbmax 600
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.6 {
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
	control.7 {
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
	control.8 {
		iface MIXER
		name 'Capture Volume'
		value.0 63
		value.1 63
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 63'
			dbmin -5100
			dbmax 1200
			dbvalue.0 1200
			dbvalue.1 1200
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
		name 'Mic Boost Volume'
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
	control.11 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 16
		value  '0fff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000   00000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.12 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 16
		value  '0f0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000   00000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.13 {
		iface MIXER
		name 'IEC958 Playback Default'
		index 16
		value  '040000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000   00000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.14 {
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
		value 103
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 127'
			dbmin -6350
			dbmax 0
			dbvalue.0 -1200
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
		iface CARD
		name 'Mic Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.19 {
		iface CARD
		name 'Speaker Front Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.20 {
		iface CARD
		name 'Speaker Surround Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.21 {
		iface CARD
		name 'Headphone Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.22 {
		iface CARD
		name 'SPDIF Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.23 {
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
	control.24 {
		iface PCM
		name 'Capture Channel Map'
		value.0 3
		value.1 4
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.25 {
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
	control.26 {
		iface CARD
		name 'HDMI/DP,pcm=3 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.27 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value  '0fff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000   00000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.28 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value  '0f0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000   00000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.29 {
		iface MIXER
		name 'IEC958 Playback Default'
		value  '040000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000   00000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.30 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.31 {
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
	control.32 {
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
	control.33 {
		iface CARD
		name 'HDMI/DP,pcm=7 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.34 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 1
		value  '0fff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000   00000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.35 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 1
		value  '0f0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000   00000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.36 {
		iface MIXER
		name 'IEC958 Playback Default'
		index 1
		value  '040000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000   00000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.37 {
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
	control.38 {
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
	control.39 {
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
	control.40 {
		iface CARD
		name 'HDMI/DP,pcm=8 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.41 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 2
		value  '0fff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000   00000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.42 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 2
		value  '0f0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000   00000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.43 {
		iface MIXER
		name 'IEC958 Playback Default'
		index 2
		value  '040000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000    0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000   00000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.44 {
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
	control.45 {
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
	control.46 {
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
	control.47 {
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
	control.48 {
		iface MIXER
		name 'Digital Capture Volume'
		value.0 120
		value.1 120
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 120'
			tlv '0000000100000008fffff44800000032'
			dbmin -3000
			dbmax 3000
			dbvalue.0 3000
			dbvalue.1 3000
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_seq_midi
snd_seq_midi_event
snd_seq
snd_rawmidi
snd_seq_device
rfcomm
bnep
binfmt_misc
arc4
brcmsmac
cordic
brcmutil
nvidia
snd_hda_codec_hdmi
b43
snd_hda_codec_cirrus
snd_hda_codec_generic
mac80211
cfg80211
applesmc
snd_hda_intel
ssb
snd_hda_codec
btusb
btrtl
btbcm
btintel
input_polldev
snd_hda_core
bluetooth
snd_hwdep
snd_pcm
input_leds
snd_timer
bcma
snd
coretemp
soundcore
kvm_intel
drm
kvm
shpchp
mac_hid
cuse
parport_pc
ppdev
lp
parport
autofs4
hid_appleir
hid_generic
hid_apple
usbhid
hid
pata_acpi
tg3
ptp
firewire_ohci
firewire_core
sdhci_pci
crc_itu_t
pps_core
ahci
sdhci
libahci
video


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x09 0x012b4040
0x0a 0x400000f0
0x0b 0x90100130
0x0c 0x018b3010
0x0d 0x400000f0
0x0e 0x400000f0
0x0f 0x01cbe020
0x10 0x014be050
0x12 0x400000f0
0x15 0x400000f0

/sys/class/sound/hwC0D0/driver_pin_configs:
0x09 0x012b4030
0x0a 0x90100121
0x0b 0x90100120
0x0c 0x400000f0
0x0d 0x90a00110
0x0e 0x400000f0
0x0f 0x400000f0
0x10 0x014be040
0x12 0x400000f0
0x15 0x400000f0

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:

/sys/class/sound/hwC0D3/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC0D3/driver_pin_configs:

/sys/class/sound/hwC0D3/user_pin_configs:

/sys/class/sound/hwC0D3/init_verbs:

/sys/class/sound/hwC0D3/hints:

/sys/class/sound/hwC0D4/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC0D4/driver_pin_configs:

/sys/class/sound/hwC0D4/user_pin_configs:

/sys/class/sound/hwC0D4/init_verbs:

/sys/class/sound/hwC0D4/hints:

/sys/class/sound/hwC0D5/init_pin_configs:
0x05 0x18560010

/sys/class/sound/hwC0D5/driver_pin_configs:

/sys/class/sound/hwC0D5/user_pin_configs:

/sys/class/sound/hwC0D5/init_verbs:

/sys/class/sound/hwC0D5/hints:


!!ALSA/HDA dmesg
!!--------------

[   12.625130] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   12.625141] snd_hda_intel 0000:00:08.0: Disabling MSI
[   12.625143] snd_hda_intel 0000:00:08.0: position_fix set to 1 for device 10de:cb89
[   12.839826] usb 4-6.2: USB disconnect, device number 5
[   12.898206] applesmc: key=215 fan=1 temp=29 index=28 acc=0 lux=0 kbd=0
[   13.796069] snd_hda_codec_cirrus hdaudioC0D0: autoconfig for CS4206: line_outs=2 (0xb/0xa/0x0/0x0/0x0) type:speaker
[   13.796076] snd_hda_codec_cirrus hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   13.796080] snd_hda_codec_cirrus hdaudioC0D0:    hp_outs=1 (0x9/0x0/0x0/0x0/0x0)
[   13.796083] snd_hda_codec_cirrus hdaudioC0D0:    mono: mono_out=0x0
[   13.796087] snd_hda_codec_cirrus hdaudioC0D0:    dig-out=0x10/0x0
[   13.796090] snd_hda_codec_cirrus hdaudioC0D0:    inputs:
[   13.796093] snd_hda_codec_cirrus hdaudioC0D0:      Mic=0xd
[   13.978422] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
--
[   14.609225] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.128  Wed Aug 26 10:41:50 PDT 2015
[   14.752673] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:08.0/sound/card0/input10
[   14.752754] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:08.0/sound/card0/input11
[   14.752827] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:08.0/sound/card0/input12
[   14.752898] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:08.0/sound/card0/input13
[   14.983413] brcmsmac bcma0:1: mfg 4bf core 812 rev 23 class 0 irq 18

 arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CS4206 Analog [CS4206 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

uname -a
Linux ######-Macmini 4.2.0-18-generic #22-Ubuntu SMP Fri Nov 6 23:32:28 UTC 2015 i686 i686 i686 GNU/Linux

---

