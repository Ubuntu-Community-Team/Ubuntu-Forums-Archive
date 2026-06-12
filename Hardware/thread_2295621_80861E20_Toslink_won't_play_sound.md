---
title: "8086:1E20 Toslink won't play sound"
date: 2015-09-20
forum: Hardware
---

### Post by maxbit89 on 2015-09-20
Hy i installed ubuntu on a pc with a Gigabyte G1 Sniper 3 (Z77 chipset) main board.

On the main board ther is a 8086:1E20 audio card.

alsa detected card and everything, i get sound when i plugin my headphones.
But when i tryed to connect my 5.1 System over Toslink i get no sound.

It seems that the toslink port is not initialized or disabled, no red light on the toslink cable (on windows there is a red light).

Can some one help plz.

Wish you all a nice day, greez maxbit89 :)

---

### Post by Yellow Pasque on 2015-09-20
Did you select digital output in the sound indicator? If it's not available, maybe you need to enable something in alsamixer:
```
alsamixer
```

Give more info if you can't figure it out: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by maxbit89 on 2015-09-20
Hy yes i selected The Digital output, but like i mentioned the toslink isn't aktive (no red light)

ALSA Info:
(Sry for upload it was to big and i think there is no spoiler tag)
> upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Sun Sep 20 21:16:49 UTC 2015


!!Linux Distribution
!!------------------

Ubuntu 14.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.3 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      To be filled by O.E.M.
Product Version:   To be filled by O.E.M.
Firmware Version:  F5


!!Kernel Information
!!------------------

Kernel release:    3.19.0-25-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.19.0-25-generic
Library version:    1.0.27.2
Utilities version:  1.0.27.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7730000 irq 34
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7080000 irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
0a:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:1e20 (rev 04)
    Subsystem: 1458:a016
--
0a:00.1 0403: 10de:0e0a (rev a1)
    Subsystem: 19da:1260


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


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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
    snoop : -1

!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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
    snoop : -1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Creative CA0132
Address: 2
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x11020011
Subsystem Id: 0x1458a016
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
  Amp-Out vals:  [0x63 0x63]
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
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="CA0132 Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
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
Node 0x07 [Audio Input] wcaps 0x10059b: Stereo Amp-In
  Device: name="CA0132 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-In vals:  [0x63 0x63]
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
  Control: name="Line Out Jack", index=0, device=0
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
  Control: name="SPDIF Phantom Jack", index=0, device=0
  Pincap 0x00000010: OUT
  Pin Default 0x014580f0: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Purple
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
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
  Control: name="Front Headphone Jack", index=0, device=0
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x02216011: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x00:
  Unsolicited: tag=10, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x03
Node 0x11 [Pin Complex] wcaps 0x40058b: Stereo Amp-In
  Control: name="Line Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02012014: [Jack] Line Out at Ext Front
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x04
Node 0x12 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Control: name="Mic1-Boost (30dB) Capture Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x37a791f0: [Jack] Mic at Oth Mobile-In
    Conn = Analog, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=12, enabled=1
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
Codec: Nvidia GPU 40 HDMI/DP
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0040
Subsystem Id: 0x19da1260
Revision Id: 0x100100
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
Node 0x04 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Connection: 4
     0x08* 0x09 0x0a 0x0b
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="HDMI/DP,pcm=7 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Control: name="ELD", index=0, device=7
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=02, enabled=1
  Connection: 4
     0x08* 0x09 0x0a 0x0b
Node 0x06 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="HDMI/DP,pcm=8 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Control: name="ELD", index=0, device=8
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=03, enabled=1
  Connection: 4
     0x08* 0x09 0x0a 0x0b
Node 0x07 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="HDMI/DP,pcm=9 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=3, device=0
  Control: name="IEC958 Playback Pro Mask", index=3, device=0
  Control: name="IEC958 Playback Default", index=3, device=0
  Control: name="IEC958 Playback Switch", index=3, device=0
  Control: name="ELD", index=0, device=9
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=04, enabled=1
  Connection: 4
     0x08* 0x09 0x0a 0x0b
Node 0x08 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x09 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x0a [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x0b [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  8 Sep 20 12:26 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  2 Sep 20 12:26 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 15 Sep 20 12:26 /dev/snd/hwC0D2
crw-rw----+ 1 root audio 116,  7 Sep 20 12:26 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116, 10 Sep 20 12:26 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  9 Sep 20 13:09 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 14 Sep 20 12:28 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116, 13 Sep 20 23:12 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116, 11 Sep 20 12:26 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116, 12 Sep 20 12:26 /dev/snd/pcmC0D4c
crw-rw----+ 1 root audio 116,  3 Sep 20 12:26 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116,  4 Sep 20 12:26 /dev/snd/pcmC1D7p
crw-rw----+ 1 root audio 116,  5 Sep 20 12:26 /dev/snd/pcmC1D8p
crw-rw----+ 1 root audio 116,  6 Sep 20 12:26 /dev/snd/pcmC1D9p
crw-rw----+ 1 root audio 116,  1 Sep 20 12:26 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Sep 20 12:26 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Sep 20 12:26 .
drwxr-xr-x 3 root root 380 Sep 20 12:26 ..
lrwxrwxrwx 1 root root  12 Sep 20 12:26 pci-0000:00:1b.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 Sep 20 12:26 pci-0000:0a:00.1 -> ../controlC1


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: CA0132 Analog Mic-In2 [CA0132 Analog Mic-In2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 4: CA0132 What U Hear [CA0132 What U Hear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [PCH]

Card hw:0 'PCH'/'HDA Intel PCH at 0xf7730000 irq 34'
  Mixer name    : 'Creative CA0132'
  Components    : 'HDA:11020011,1458a016,00100918'
  Controls      : 45
  Simple ctrls  : 25
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 99
  Mono:
  Front Left: Playback 99 [100%] [9.00dB] [on]
  Front Right: Playback 99 [100%] [9.00dB] [on]
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
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
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

!!-------Mixer controls for card 1 [NVidia]

Card hw:1 'NVidia'/'HDA NVidia at 0xf7080000 irq 17'
  Mixer name    : 'Nvidia GPU 40 HDMI/DP'
  Components    : 'HDA:10de0040,19da1260,00100100'
  Controls      : 28
  Simple ctrls  : 4
Simple mixer control 'IEC958',0
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
Simple mixer control 'IEC958',3
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
        name 'Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.28 {
        iface CARD
        name 'Line Jack'
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
        iface CARD
        name 'Front Headphone Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.31 {
        iface CARD
        name 'SPDIF Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.32 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.33 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.34 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write locked'
            type IEC958
            count 1
        }
    }
    control.35 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.36 {
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.37 {
        iface MIXER
        name 'IEC958 Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.38 {
        iface MIXER
        name 'IEC958 Capture Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.39 {
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
    control.40 {
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
    control.41 {
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
    control.42 {
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
    control.43 {
        iface PCM
        device 1
        name 'Playback Channel Map'
        value.0 3
        value.1 4
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.44 {
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
    control.45 {
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
state.NVidia {
    control.1 {
        iface CARD
        name 'HDMI/DP,pcm=3 Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.5 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.6 {
        iface PCM
        device 3
        name ELD
        value '100008006d10000100000100000000000472f10054323330480a20202020202020097f070000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read volatile'
            type BYTES
            count 95
        }
    }
    control.7 {
        iface CARD
        name 'HDMI/DP,pcm=7 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.8 {
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
    control.9 {
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
    control.10 {
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
    control.11 {
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
    control.12 {
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
    control.13 {
        iface CARD
        name 'HDMI/DP,pcm=8 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.14 {
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
    control.15 {
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
    control.16 {
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
    control.17 {
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
    control.18 {
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
    control.19 {
        iface CARD
        name 'HDMI/DP,pcm=9 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.20 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 3
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.21 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 3
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.22 {
        iface MIXER
        name 'IEC958 Playback Default'
        index 3
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.23 {
        iface MIXER
        name 'IEC958 Playback Switch'
        index 3
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.24 {
        iface PCM
        device 9
        name ELD
        value ''
        comment {
            access 'read volatile'
            type BYTES
            count 0
        }
    }
    control.25 {
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
    control.26 {
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
    control.27 {
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
    control.28 {
        iface PCM
        device 9
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
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ctr
ccm
bnep
rfcomm
bluetooth
snd_hda_codec_hdmi
snd_hda_codec_ca0132
snd_seq_midi
snd_seq_midi_event
mxm_wmi
snd_hda_intel
intel_rapl
iosf_mbi
snd_hda_controller
x86_pkg_temp_thermal
nvidia
snd_hda_codec
intel_powerclamp
snd_hwdep
coretemp
arc4
snd_rawmidi
kvm_intel
snd_pcm
ath9k
kvm
ath9k_common
ath9k_hw
crct10dif_pclmul
crc32_pclmul
ath
ghash_clmulni_intel
mac80211
snd_seq
aesni_intel
aes_x86_64
joydev
lrw
gf128mul
serio_raw
cfg80211
glue_helper
ablk_helper
snd_seq_device
cryptd
snd_timer
snd
drm
lpc_ich
soundcore
tpm_infineon
wmi
video
mac_hid
mei_me
ie31200_edac
shpchp
mei
edac_core
parport_pc
ppdev
lp
parport
uas
usb_storage
hid_generic
usbhid
hid
e1000e
firewire_ohci
psmouse
firewire_core
alx
ahci
ptp
mdio
crc_itu_t
libahci
pps_core


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D2/init_pin_configs:
0x0b 0x010140f0
0x0c 0x014520f0
0x0d 0x414570f0
0x0e 0x41c510f0
0x0f 0x412170f0
0x10 0x022140f0
0x11 0x018110f0
0x12 0x01a190f0
0x13 0x50d000f0
0x18 0x500000f0

/sys/class/sound/hwC0D2/driver_pin_configs:

/sys/class/sound/hwC0D2/user_pin_configs:

/sys/class/sound/hwC0D2/init_verbs:

/sys/class/sound/hwC0D2/hints:

/sys/class/sound/hwC1D0/init_pin_configs:
0x04 0x185600f0
0x05 0x185600f0
0x06 0x185600f0
0x07 0x185600f0

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D0/hints:


!!ALSA/HDA dmesg
!!--------------

[    2.361743] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.82  Wed Jun 17 10:37:46 PDT 2015
[    2.363547] snd_hda_intel 0000:0a:00.1: Disabling MSI
[    2.363552] snd_hda_intel 0000:0a:00.1: Handle VGA-switcheroo audio client
[    2.373697] sound hdaudioC0D2: autoconfig: line_outs=1 (0xb/0x0/0x0/0x0/0x0) type:line
[    2.373700] sound hdaudioC0D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    2.373701] sound hdaudioC0D2:    hp_outs=1 (0x10/0x0/0x0/0x0/0x0)
[    2.373702] sound hdaudioC0D2:    mono: mono_out=0x0
[    2.373703] sound hdaudioC0D2:    dig-out=0xc/0x0
[    2.373704] sound hdaudioC0D2:    inputs:
[    2.373706] sound hdaudioC0D2:      Mic=0x12
[    2.373707] sound hdaudioC0D2:      Line=0x11
[    2.383139] cfg80211: World regulatory domain updated:
--
[    2.568408] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    2.823013] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:08:00.0/0000:09:10.0/0000:0a:00.1/sound/card1/input7
[    2.823054] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:08:00.0/0000:09:10.0/0000:0a:00.1/sound/card1/input8
[    2.823087] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:08:00.0/0000:09:10.0/0000:0a:00.1/sound/card1/input9
[    2.823160] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:08:00.0/0000:09:10.0/0000:0a:00.1/sound/card1/input10
[    2.906147] EXT4-fs (sde5): mounted filesystem with ordered data mode. Opts: (null)
--
[    3.102102] init: cups main process ended, respawning
[    3.180742] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    3.181340] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    3.181430] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    3.181532] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    3.315451] init: alsa-restore main process (1181) terminated with status 99



---

### Post by Yellow Pasque on 2015-09-20
I would try and toggle this setting in alsamixer:
```
Simple mixer control 'IEC958 Default PCM',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
```


> think there is no spoiler tag
Use code tags for large blocks of text (and to preserve whitespace).

---

