---
title: "ASUS U52F Laptop Headphone Jack Not Recognized"
date: 2011-02-10
forum: Hardware
---

### Post by Iamnotsteve on 2011-02-10
As the title says, my front (and only) headphone jacks are not being recognised. It makes no difference whether they're plugged in or not, nothing happens. I've messed around with other solutions posted in the forums, but none have worked. Despite [this fellow]("http://ubuntuforums.org/showthread.php?t=1655563&highlight=sound+headphones+speakers") having nearly the same Audio Device as me, nothing took.

I've also messed around with alsamixer, and no channels are muted. Changing the outputs in the sound preferences either result in no change or a complete loss of sound (the latter occurring when the Analog Headphones option is selected.)

```
lspci|grep Audio
```00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

Alsa Info:

```
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Thu Feb 10 09:18:57 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      ASUSTeK Computer Inc.        
Product Name:      U52F
Product Version:   1.0       


!!Kernel Information
!!------------------

Kernel release:    2.6.35-25-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


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
                      HDA Intel at 0xd4000000 irq 45


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 06)
    Subsystem: 1043:1283


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
snd-hda-intel: model=hp-laptop
snd-hda-intel: model=hp-dv5 enable_msi=1


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : 1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : hp-dv5,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC259
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0269
Subsystem Id: 0x10431283
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC259 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x41 0x41]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x41 0x41]
  Converter: stream=5, channel=0
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
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x9f 0x9f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
  Control: name="Capture Switch", index=0, device=0
  Control: name="Mic Boost", index=0, device=0
  Control: name="IntMic Boost", index=0, device=0
  Device: name="ALC259 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x8b 0x8b]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x18 0x19 0x1a 0x1b 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x80]
  Connection: 2
     0x02 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x40000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
Node 0x16 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x17 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01a19820: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=08, enabled=1
  Connection: 1
     0x0d
Node 0x19 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Control: name="IntMic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x99a3092f: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x2, Sequence = 0xf
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40079a2d: [N/A] Line Out at Ext N/A
    Conn = Analog, Color = Pink
    DefAssociation = 0x2, Sequence = 0xd
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=25
Node 0x21 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0121441f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x22 [Audio Selector] wcaps 0x30010b: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  Connection: 7
     0x18 0x19* 0x1a 0x1b 0x1d 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
Codec: Intel IbexPeak HDMI
Address: 3
Function Id: 0x1
Vendor Id: 0x80862804
Subsystem Id: 0x80860101
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
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="INTEL HDMI 0", type="HDMI", device=3
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="INTEL HDMI 1", type="HDMI", device=7
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x04 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560010: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x02* 0x03
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560020: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x02* 0x03
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560030: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=06, enabled=1
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x02* 0x03
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 10 Feb 10 02:53 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  9 Feb 10 02:53 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  8 Feb 10 02:53 /dev/snd/hwC0D3
crw-rw----+ 1 root audio 116,  7 Feb 10 02:55 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  6 Feb 10 02:55 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  5 Feb 10 02:55 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  4 Feb 10 02:53 /dev/snd/pcmC0D7p
crw-rw----+ 1 root audio 116,  3 Feb 10 02:53 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Feb 10 02:53 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Feb 10 02:53 .
drwxr-xr-x 3 root root 240 Feb 10 02:53 ..
lrwxrwxrwx 1 root root  12 Feb 10 02:53 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xd4000000 irq 45'
  Mixer name    : 'Intel IbexPeak HDMI'
  Components    : 'HDA:10ec0269,10431283,00100100 HDA:80862804,80860101,00100000'
  Controls      : 19
  Simple ctrls  : 9
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 65 [75%] [-16.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 252 [99%] [0.60dB]
  Front Right: Playback 252 [99%] [0.60dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [off]
  Front Right: Capture 31 [100%] [30.00dB] [off]
Simple mixer control 'IntMic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 true
        value.1 true
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 87'
        comment.dbmin -6525
        comment.dbmax 0
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 87
        value.1 87
    }
    control.3 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 87'
        comment.dbmin -6525
        comment.dbmax 0
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 87
        value.1 87
    }
    control.5 {
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
    control.6 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 false
        value.1 false
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3600
        iface MIXER
        name 'Mic Boost'
        value.0 0
        value.1 0
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3600
        iface MIXER
        name 'IntMic Boost'
        value.0 0
        value.1 0
    }
    control.9 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 87'
        comment.dbmin -6525
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value 65
    }
    control.10 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.11 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.12 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.13 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
    control.15 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 1
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.16 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 1
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.17 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        index 1
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        index 1
        value true
    }
    control.19 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 252
        value.1 252
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
parport_pc
ppdev
binfmt_misc
snd_hda_codec_intelhdmi
snd_hda_codec_realtek
joydev
i915
snd_hda_intel
snd_hda_codec
arc4
drm_kms_helper
snd_hwdep
drm
iwlagn
snd_pcm
snd_seq_midi
iwlcore
snd_rawmidi
i2400m_usb
snd_seq_midi_event
i2400m
snd_seq
mac80211
wimax
uvcvideo
snd_timer
snd_seq_device
videodev
v4l1_compat
v4l2_compat_ioctl32
i2c_algo_bit
snd
psmouse
serio_raw
cfg80211
asus_laptop
sparse_keymap
video
intel_ips
led_class
output
soundcore
snd_page_alloc
intel_agp
lp
parport
usbhid
hid
ahci
atl1c
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x12 0x411111f0
0x14 0x99130110
0x17 0x411111f0
0x18 0x01a19820
0x19 0x99a3092f
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x40079a2d
0x1e 0x411111f0
0x21 0x0121441f

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D3/init_pin_configs:
0x04 0x58560010
0x05 0x18560020
0x06 0x58560030

/sys/class/sound/hwC0D3/driver_pin_configs:

/sys/class/sound/hwC0D3/user_pin_configs:

/sys/class/sound/hwC0D3/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   17.528571]   alloc kstat_irqs on node -1
[   17.528583] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.528685]   alloc irq_desc for 45 on node -1
[   17.528688]   alloc kstat_irqs on node -1
[   17.528703] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   17.528745] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.548018] elantech: Synaptics capabilities query result 0x78, 0x16, 0x0d.


```
I'd really appreciate any help the community can give me. This isn't a huge issue, but I would very much like to get it resolved in the near future.

---

### Post by Iamnotsteve on 2011-02-14
Bumping this for better chance of assistance.

---

### Post by Iamnotsteve on 2011-02-21
Bumping again. I'd really appreciate if someone could assist me. This issue is the main reason that I am using Windows7 as opposed to this right now. I would very much like to resolve this problem.

---

### Post by recken on 2011-02-23
Same here with the ASUS K52JC ... same soundcard as well

It seems ASUS just isn't ubuntu friendly

---

### Post by firefox_user2 on 2011-03-13
> **Iamnotsteve said:**
> Bumping again. I'd really appreciate if someone could assist me. This issue is the main reason that I am using Windows7 as opposed to this right now. I would very much like to resolve this problem.
I have the same Laptop with the same problem. I have tried everything in the posts without success. I finally quit trying because I was afraid of messing up something.

I am hoping the next Ubuntu version clears this up as there seems to be quite a few others with the same problem.
Just wanted to let you know you are not alone and I am still searching for a fix.
Have a nice day.

---

### Post by recken on 2011-03-14
It seems the problem sorted itself ... but I don't really now how

I upgraded to Ubuntu 10.10 and updated it completely. This in itself didn't work, but then I ran alsamixer to set the volume and since then everything is working 100%, even after several reboots.

---

### Post by firefox_user2 on 2011-07-02
OK...Finally solved.

I read and logged every suggestion I could find to fix this problem and then proceeded to try each one, one after the other.
On about the third try I hit the magic solution and now the speakers and headphone jack work like they are supposed to.

For me, the solution was as follows.

In Terminal: sudo gedit/etc/modprobe.d/alsa-base.conf

Add the following line:  options snd-hda-intel model=auto
Save and reboot.

Thanks to all that submitted solutions, there is a way to fix this after all. Just keep trying fellow Ubunters.

---

### Post by sbuxhofer on 2011-07-13
Problem got solved for me adding the quoted config to the alsa-base.conf modprobe files and following this post ([http://girliemangalo.wordpress.com/2011/04/15/fix-asus-k52j-speaker-sounds-with-ubuntu-10-10/](http://girliemangalo.wordpress.com/2011/04/15/fix-asus-k52j-speaker-sounds-with-ubuntu-10-10/)) to fix the headphone plug issue on my asus u52f running ubuntu 10.04.

Solution asus u52f - ubuntu 10.04.:

1. In your terminal, add the ppa
 sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
 sudo apt-get update
 2. Install the linux-alsa-driver-modules package
 sudo apt-get install linux-alsa-driver-modules-$(uname -r)
3. sudo gedit/etc/modprobe.d/alsa-base.conf
Add the following line:  options snd-hda-intel model=auto
 4. Restart your machine


> **firefox_user2 said:**
> OK...Finally solved.

I read and logged every suggestion I could find to fix this problem and then proceeded to try each one, one after the other.
On about the third try I hit the magic solution and now the speakers and headphone jack work like they are supposed to.

For me, the solution was as follows.

In Terminal: sudo gedit/etc/modprobe.d/alsa-base.conf

Add the following line:  options snd-hda-intel model=auto
Save and reboot.

Thanks to all that submitted solutions, there is a way to fix this after all. Just keep trying fellow Ubunters.

---

### Post by Iamnotsteve on 2011-07-16
At the bequest of lidex I have gotten around to reinstalling Ubuntu and returned to the thread (which, frankly, I had completely forgotten about) to hopefully get this thing sorted out proper.

The Good News: The update while I was away added some slick new interface fun and my computer no longer continues to play music on my speakers after I plug in my headphones.

The Bad News: My computer doesn't play music (or any other sounds) at all. And I've lost what little competency I had with the OS in the downtime.

I'm happy to see that a few of you had some luck with the problem; I'll be trying those options once I get back home in a few days. I'll provide another alsa dump then too.

---

### Post by vaultman88 on 2012-01-05
Thank you, thank you, thank you! You guys rock! I've been searching for a few days! I have a ASUS G72X with an Intel Corporation 82801JI (ICH10 Family) HD Audio Controller (found by typing in lspci in the terminal). I followed the above instructions and got it so that my speakers would be the only sound to come out, which is better than before when both the speakers and the headphones both played sounds. To get the headphones to work I had to go into Phonon-KDE Control Module and set it to headphones under the pull down menu Connector. Then in terminal I went to alsamixer and cranked all the volumes up to 100%. Now it works! 
I'm running KDE 4.7.4 so the sudo gedit command didn't work right off the bat. To alter this file I had to cd directories right down to modprob.d and from there sudo gedit ./alsa-base.conf

I hope this helps! Thanks Again Guys!

---

### Post by fieloryb on 2012-08-17
For Asus K52F solution is:

1. (in terminal)
```

~$ sudo gedit /etc/modprobe.d/alsa-base.conf

``` {password}
2. add last line:
```

options snd-hda-intel model=z71v position_fix=1

```
3. restart 'puter
[[COLOR="Red"]Source[/COLOR]]("http://www.physicsforums.com/blog.php?b=2580")

---

### Post by fieloryb on 2012-09-16
Other solution is installing Alsa 1.0.23

[source]("http://codingchyne.wordpress.com/2010/10/12/fixing-earphones-problem-on-ubuntu-10-04/")
and add
```

options snd-hda-intel model=ideapad

```
to:
```

sudo gedit /etc/modprobe.d/alsa-base.conf

```

---

