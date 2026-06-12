---
title: "Sony Vaio VGX-XL100 audio problems"
date: 2014-05-27
forum: Hardware
---

### Post by BellsWhistles on 2014-05-27
I have a Sony VAIO VGX-XL100 that I have installed Lubuntu on.

Everything is ok except the audio is not working.

The audio is very, very faint and is heard through an external amp through any channel so it appears more like interference rather than a direct link. Varying the volume and muting does work but only with that very faint sound.

My attempts so far include

[LIST]
[*]boosting all volume on all the channels
[*]trying Ubuntu from disk - same symptom
[*]editing the /etc/modprobe.d/alsa-base to add options snd-hda-intel index=0 model=vaio
[*]Choosing different combinations from the Alsamixer to see if its muted
[/LIST]

I'm sure I'm missing something obvious

Has anyone installed on this machine? It is one of those an odd Sony Media Centers.

One of those
[https://www.google.co.uk/search?q=Sony+VAIO+VGX-XL100&rls=com.microsoft:en-gb:IE-Address&source=lnms&tbm=isch&sa=X&ei=gmuEU5feBsPH7Aab3IA4&ved=0CAkQ_AUoAg&biw=1280&bih=879](https://www.google.co.uk/search?q=Sony+VAIO+VGX-XL100&rls=com.microsoft:en-gb:IE-Address&source=lnms&tbm=isch&sa=X&ei=gmuEU5feBsPH7Aab3IA4&ved=0CAkQ_AUoAg&biw=1280&bih=879)


thanks

---

### Post by Yellow Pasque on 2014-05-27
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by BellsWhistles on 2014-05-27
That's how it went.

[http://www.alsa-project.org/db/?f=58494a2012f11e6eebf2c2ad77904f1006651287](http://www.alsa-project.org/db/?f=58494a2012f11e6eebf2c2ad77904f1006651287)

```

!!################################
!!ALSA Information Script v 0.4.63
!!################################

!!Script ran on: Tue May 27 22:07:43 UTC 2014


!!Linux Distribution
!!------------------

Ubuntu 14.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      Sony Corporation
Product Name:      VGX-XL100
Product Version:   C4205XN3
Firmware Version:  2001 


!!Kernel Information
!!------------------

Kernel release:    3.13.0-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.13.0-24-generic
Library version:    1.0.27.2
Utilities version:  1.0.27.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
saa7134_alsa


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff8000 irq 45
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xfdbfe000 irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
04:05.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
    Subsystem: 104d:81f7


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
snd_hda_intel: index=0 model=generic


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : 0,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    model : generic,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : Y

!!Module: saa7134_alsa
    debug : 0
    enable : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
    index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: SigmaTel ID 7661
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x83847661
Subsystem Id: 0x104d0b00
Revision Id: 0x104201
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
GPIO: io=5, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ID 7661 Analog", type="Audio", device=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=8, channel=0
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x03 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Converter: stream=0, channel=0
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x04 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Converter: stream=0, channel=0
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x05 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=8, channel=0
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x06 [Audio Input] wcaps 0x1d0541: Stereo
  Device: name="ID 7661 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power states: 
  Power: setting=D0, actual=D0
  Delay: 13 samples
  Connection: 1
     0x07
  Processing caps: benign=0, ncoeff=0
Node 0x07 [Audio Selector] wcaps 0x300903: Stereo Amp-In R/L
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00]
  Connection: 1
     0x0e
Node 0x08 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=4, channel=0
  SDI-Select: 0
  Power states: 
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
  Amp-In vals:  [0x00 0x00]
  Connection: 1
     0x15
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Control: name="Front Line Out Front Phantom Jack", index=0, device=0
  Pincap 0x0000173c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02024110: [Jack] Line Out at Ext Front
    Conn = 1/4, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
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
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x03
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Control: name="Mic Phantom Jack", index=0, device=0
  Pincap 0x0000173c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a19920: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Control: name="Line Phantom Jack", index=0, device=0
  Pincap 0x00000024: IN Detect
  Pin Default 0x01845121: [Jack] Line In at Ext Rear
    Conn = RCA, Color = Red
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Control: name="Line Out Surround Phantom Jack", index=0, device=0
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01045111: [Jack] Line Out at Ext Rear
    Conn = RCA, Color = Red
    DefAssociation = 0x1, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x05
Node 0x10 [Audio Output] wcaps 0x40211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ID 7661 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x3e0]: 44100 48000 88200 96000 176400
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x11 [Pin Complex] wcaps 0x400301: Stereo Digital
  Control: name="SPDIF Phantom Jack", index=0, device=0
  Pincap 0x00000010: OUT
  Pin Default 0x01451112: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 2
     0x10* 0x09
Node 0x12 [Audio Input] wcaps 0x140311: Stereo Digital
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Device: name="ID 7661 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
  Connection: 1
     0x13
Node 0x13 [Pin Complex] wcaps 0x440381: Stereo Digital
  Control: name="SPDIF In Phantom Jack", index=0, device=0
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x01c51122: [Jack] SPDIF In at Ext Rear
    Conn = Optical, Color = Black
    DefAssociation = 0x2, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Delay: 4 samples
  Connection: 1
     0x18
Node 0x14 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x15 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=1
  Amp-Out vals:  [0x00 0x00]
  Connection: 4
     0x0a 0x0d* 0x14 0x02
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
  IEC Coding Type: 0x0
  Delay: 4 samples
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  9 May 27 20:47 /dev/snd/controlC0
crw-rw----  1 root audio 116,  3 May 27 20:47 /dev/snd/controlC1
crw-rw----  1 root audio 116,  8 May 27 20:47 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  7 May 27 20:48 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  6 May 27 20:48 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  5 May 27 20:48 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116,  4 May 27 20:48 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  2 May 27 20:48 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116,  1 May 27 20:47 /dev/snd/seq
crw-rw----  1 root audio 116, 33 May 27 20:47 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 May 27 20:47 .
drwxr-xr-x 3 root root 260 May 27 20:47 ..
lrwxrwxrwx 1 root root  12 May 27 20:47 pci-0000:00:1b.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 May 27 20:47 pci-0000:04:05.0 -> ../controlC1


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ID 7661 Analog [ID 7661 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ID 7661 Digital [ID 7661 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ID 7661 Analog [ID 7661 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ID 7661 Digital [ID 7661 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfdff8000 irq 45'
  Mixer name    : 'SigmaTel ID 7661'
  Components    : 'HDA:83847661,104d0b00,00104201'
  Controls      : 29
  Simple ctrls  : 11
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]

!!-------Mixer controls for card 1 [SAA7134]

Card hw:1 'SAA7134'/'saa7133[0] at 0xfdbfe000 irq 17'
  Mixer name    : 'SAA7134 Mixer'
  Components    : ''
  Controls      : 6
  Simple ctrls  : 3
Simple mixer control 'Line',1
  Capabilities: volume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 20
  Front Left: 20 [100%] Capture [on]
  Front Right: 20 [100%] Capture [on]
Simple mixer control 'Line',2
  Capabilities: volume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 20
  Front Left: 20 [100%] Capture [off]
  Front Right: 20 [100%] Capture [off]
Simple mixer control 'Video',0
  Capabilities: volume cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 20
  Front Left: 20 [100%] Capture [off]
  Front Right: 19 [95%] Capture [off]


!!Alsactl output
!!--------------

--startcollapse--
state.Intel {
    control.1 {
        iface MIXER
        name 'Front Playback Volume'
        value.0 127
        value.1 127
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 127'
            dbmin -9525
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
        value.0 127
        value.1 127
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 127'
            dbmin -9525
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
        name 'Capture Source'
        value Mic
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mic
            item.1 Line
        }
    }
    control.6 {
        iface MIXER
        name 'Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 15'
            dbmin 0
            dbmax 2250
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.7 {
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
    control.8 {
        iface MIXER
        name 'Mic Boost Volume'
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
    control.9 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.10 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.11 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.12 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.13 {
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.14 {
        iface MIXER
        name 'IEC958 Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.15 {
        iface MIXER
        name 'IEC958 Capture Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.16 {
        iface MIXER
        name 'Master Playback Volume'
        value 127
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 127'
            dbmin -9525
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
        name 'Line Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.20 {
        iface CARD
        name 'Front Line Out Front Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.21 {
        iface CARD
        name 'Line Out Surround Phantom Jack'
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
        iface CARD
        name 'SPDIF In Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.24 {
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
    control.25 {
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
    control.26 {
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
    control.27 {
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
    control.28 {
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
    control.29 {
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
state.SAA7134 {
    control.1 {
        iface MIXER
        name 'Video Volume'
        value.0 20
        value.1 19
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 20'
        }
    }
    control.2 {
        iface MIXER
        name 'Line Volume'
        index 1
        value.0 20
        value.1 20
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 20'
        }
    }
    control.3 {
        iface MIXER
        name 'Line Volume'
        index 2
        value.0 20
        value.1 20
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 20'
        }
    }
    control.4 {
        iface MIXER
        name 'Video Capture Switch'
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
        name 'Line Capture Switch'
        index 1
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
        name 'Line Capture Switch'
        index 2
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
bnep
bluetooth
kvm_intel
snd_hda_intel
kvm
saa7134_alsa
ir_lirc_codec
lirc_dev
ir_sony_decoder
ir_mce_kbd_decoder
ir_sanyo_decoder
ir_rc5_decoder
ir_jvc_decoder
ir_rc6_decoder
ir_nec_decoder
rc_rc6_mce
snd_hda_codec
mceusb
joydev
saa7134
snd_hwdep
snd_pcm
snd_page_alloc
serio_raw
snd_seq_midi
tveeprom
snd_seq_midi_event
videobuf_dma_sg
rc_core
nvidia
v4l2_common
snd_rawmidi
videobuf_core
videodev
lpc_ich
snd_seq
snd_seq_device
snd_timer
sony_laptop
parport_pc
snd
mac_hid
soundcore
ppdev
lp
parport
hid_sony
ff_memless
usbhid
hid
usb_storage
firewire_ohci
psmouse
ahci
libahci
e1000e
firewire_core
crc_itu_t
ptp
pps_core


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0a 0x02024110
0x0b 0x411111f0
0x0c 0x411111f0
0x0d 0x02a19920
0x0e 0x01845121
0x0f 0x01045111
0x11 0x01451112
0x13 0x01c51122
0x14 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:


!!ALSA/HDA dmesg
!!--------------

[   15.396419] IR LIRC bridge handler initialized
[   15.397440] saa7134 ALSA driver for DMA sound loaded
[   15.397488] saa7133[0]/alsa: saa7133[0] at 0xfdbfe000 irq 17 registered as card -2
--
[   15.405477] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[   15.425695] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   15.478725] autoconfig: line_outs=2 (0xa/0xf/0x0/0x0/0x0) type:line

```

---

### Post by BellsWhistles on 2014-05-29
I've added that there. Is that correct? Am I missing any obvious issue? thanks.

---

### Post by Yellow Pasque on 2014-05-29
I personally don't see anything obvious. Did you try headphones?

You may want to file a bug on this one (make sure you remove model=generic before you do).

---

### Post by matt_symes on 2014-05-29
Hi

I would have a play with 

```
hda-jack-retask
```

from Henningsson's ppa ([https://launchpad.net/~diwic/+archive/hda](https://launchpad.net/~diwic/+archive/hda)).

You may be able to retask the pin configuration for the codec for the correct jack and get better sound.

I'm wondering if the EAPD pin (external amplifier) is being set incorrectly.

But as stated, raise a bug report.

```
ubuntu-bug audio
```

Kind regards

---

### Post by Yellow Pasque on 2014-05-29
> **matt_symes said:**
> I'm wondering if the EAPD pin (external amplifier) is being set incorrectly.

That's why I asked about headphone function. Usually, when there's EAPD issue, headphones still work.

---

### Post by BellsWhistles on 2014-06-04
So under the generic model I can get a very quiet almost adequate signal from the front headphone jack.

All other sockets only give only a tiny interference level signal.

There is one heaphone socket on the front.
Also on the front are RCA sinput jacks.

On the back there are input and output RCA jacks.

Its the out put jacks on the back that I miss audio from.

I've tried hda-jack-retask but I couldn't find any combination that activated it.

I'll do the bug report next.

---

