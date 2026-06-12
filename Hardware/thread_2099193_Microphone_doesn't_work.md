---
title: "Microphone doesn't work"
date: 2012-12-28
forum: Hardware
---

### Post by srekcahrai on 2012-12-28
Hi,
  I have a HP Pavilion dv4 Notebook. I have dual-boot of Win 7 and Ubuntu 12.10. My Built-in microphone seems to be working in windows OS but it doesn't work in Ubuntu.
In system settings > sound > input there are three options Microphone, Analog input/Line in and Analog input/Microphone.

I used an external microphone and tested in all three options.
Microphone - It recorded only buzz noise and hardly my voice
Analog input/Line - Nothing
Analog input/Microphone - It recorded my proper voice

---

### Post by lisati on 2012-12-29
*Thread moved to **Hardware**.*

---

### Post by srekcahrai on 2013-01-29
bump

---

### Post by Yellow Pasque on 2013-01-29
Please post the link to your alsa info:  [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by srekcahrai on 2013-01-29
> **Temüjin said:**
> Please post the link to your alsa info:  [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Here is the result:
```


upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.61
!!################################

!!Script ran on: Tue Jan 29 18:53:43 UTC 2013


!!Linux Distribution
!!------------------

Ubuntu 12.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu quantal (12.10)"


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP Pavilion dv4 Notebook PC
Product Version:   1
Firmware Version:  F.42


!!Kernel Information
!!------------------

Kernel release:    3.5.0-17-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         athlon
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.25
Library version:    1.0.25
Utilities version:  1.0.25


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

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0x92500000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0x92410000 irq 19


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS780 HDMI Audio [Radeon HD 3000-3300 Series]


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:14.2 0403: 1002:4383
    Subsystem: 103c:30fb
--
01:05.1 0403: 1002:960f
    Subsystem: 1002:960f


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
snd-hda-intel: model=dell-m4-1
snd-hda-intel: enable_msi=1


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : Y

!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : Y


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: IDT 92HD71B7X
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x111d76b2
Subsystem Id: 0x103c361f
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=8, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[5]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[6]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[7]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Power-Map: 0x05
Analog Loopback: 0x00
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Control: name="Front Headphone Jack", index=0, device=0
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x02214010: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Connection: 3
     0x10 0x11* 0x17
Node 0x0b [Pin Complex] wcaps 0x400081: Stereo
  Control: name="Mic Jack Mode", index=0, device=0
    ControlAmp: chs=0, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a19020: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
Node 0x0c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x40f100f0: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Control: name="Speaker Phantom Jack", index=0, device=0
  Pincap 0x00000014: OUT Detect
  Pin Default 0x90170010: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10* 0x11 0x17
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x40f100f2: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x2
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x40f100f3: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x3
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10* 0x11 0x17
Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=63
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="STAC92xx Analog", type="Audio", device=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=8, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=63
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Converter: stream=8, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x12 [Audio Input] wcaps 0x1d0541: Stereo
  Device: name="STAC92xx Analog", type="Audio", device=0
  Converter: stream=4, channel=0
  SDI-Select: 0
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x1c
  Processing caps: benign=0, ncoeff=0
Node 0x13 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x1d
  Processing caps: benign=0, ncoeff=0
Node 0x14 [Pin Complex] wcaps 0x400100: Mono
  Pincap 0x00000010: OUT
  Pin Default 0x40f100f4: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x4
  Pin-ctls: 0x00:
  Connection: 1
     0x16
Node 0x15 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x10* 0x11 0x17
Node 0x16 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x15
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x10 0x11 0x27 0x1a 0x1b
Node 0x18 [Pin Complex] wcaps 0x40000d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40f100f5: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x5
  Pin-ctls: 0x20: IN
Node 0x19 [Pin Complex] wcaps 0x40000d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40f100f6: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x6
  Pin-ctls: 0x00:
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Mux Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Mux Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x01 0x00]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x0f 0x0f]
  Connection: 4
     0x1a* 0x17 0x18 0x19
Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x8f 0x8f]
  Connection: 4
     0x1b* 0x17 0x18 0x19
Node 0x1e [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f100f7: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x7
  Pin-ctls: 0x00:
  Connection: 1
     0x24
Node 0x1f [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00010010: OUT EAPD
  EAPD 0x0:
  Pin Default 0x40f100f8: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x8
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 2
     0x24* 0x25
Node 0x20 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f100f9: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x9
  Pin-ctls: 0x00:
  Connection: 1
     0x25
Node 0x21 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x22 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x23 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x21* 0x1c 0x1d
Node 0x25 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x22* 0x1c 0x1d
Node 0x26 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Node 0x27 [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40f100fa: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xa
  Pin-ctls: 0x00:
Node 0x28 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=1, val=127
  Connection: 2
     0x10 0x11
Codec: LSI ID 1040
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x11c11040
Subsystem Id: 0x103c137e
Revision Id: 0x100200
Modem Function Group: 0x1
Codec: ATI RS690/780 HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002791a
Subsystem Id: 0x00791a00
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x40]: 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=1, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  6 Jan 29 23:14 /dev/snd/controlC0
crw-rw---T+ 1 root audio 116,  9 Jan 29 23:14 /dev/snd/controlC1
crw-rw---T+ 1 root audio 116,  5 Jan 29 23:14 /dev/snd/hwC0D0
crw-rw---T+ 1 root audio 116,  4 Jan 29 23:14 /dev/snd/hwC0D1
crw-rw---T+ 1 root audio 116,  8 Jan 29 23:14 /dev/snd/hwC1D0
crw-rw---T+ 1 root audio 116,  3 Jan 30 00:22 /dev/snd/pcmC0D0c
crw-rw---T+ 1 root audio 116,  2 Jan 30 00:21 /dev/snd/pcmC0D0p
crw-rw---T+ 1 root audio 116,  7 Jan 30 00:21 /dev/snd/pcmC1D3p
crw-rw---T+ 1 root audio 116,  1 Jan 30 00:21 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Jan 29 23:14 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Jan 29 23:14 .
drwxr-xr-x 3 root root 260 Jan 29 23:14 ..
lrwxrwxrwx 1 root root  12 Jan 29 23:14 pci-0000:00:14.2 -> ../controlC0
lrwxrwxrwx 1 root root  12 Jan 29 23:14 pci-0000:01:05.1 -> ../controlC1


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0x92500000 irq 16'
  Mixer name    : 'IDT 92HD71B7X'
  Components    : 'HDA:111d76b2,103c361f,00100302 HDA:11c11040,103c137e,00100200'
  Controls      : 21
  Simple ctrls  : 12
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'Digital Playback' 'Analog Mux 1' 'Analog Mux 2'
  Item0: 'Digital Playback'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [off]
  Front Right: Capture 15 [100%] [22.50dB] [off]
Simple mixer control 'Mute-LED Mode',0
  Capabilities: enum
  Items: 'Off' 'On' 'Follow Master'
  Item0: 'Follow Master'
Simple mixer control 'Mux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 1 [33%] [10.00dB]
  Front Right: Capture 0 [0%] [0.00dB]

!!-------Mixer controls for card 1 [HDMI]

Card hw:1 'HDMI'/'HDA ATI HDMI at 0x92410000 irq 19'
  Mixer name    : 'ATI RS690/780 HDMI'
  Components    : 'HDA:1002791a,00791a00,00100000'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.SB {
    control.1 {
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 64
        value.1 64
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 64'
            dbmin -4800
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.2 {
        iface MIXER
        name 'Speaker Playback Switch'
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
        name 'Mic Jack Mode'
        value 'Mic In'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 'Mic In'
            item.1 'Line In'
        }
    }
    control.4 {
        iface MIXER
        name 'Beep Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.5 {
        iface MIXER
        name 'Beep Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 3'
            dbmin -1800
            dbmax 0
            dbvalue.0 -1800
        }
    }
    control.6 {
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 64
        value.1 64
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 64'
            dbmin -4800
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.7 {
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
    control.8 {
        iface MIXER
        name 'Capture Volume'
        value.0 15
        value.1 15
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 15'
            dbmin 0
            dbmax 2250
            dbvalue.0 2250
            dbvalue.1 2250
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
        name 'Capture Volume'
        index 1
        value.0 15
        value.1 15
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 15'
            dbmin 0
            dbmax 2250
            dbvalue.0 2250
            dbvalue.1 2250
        }
    }
    control.11 {
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
    control.12 {
        iface MIXER
        name 'Mux Capture Volume'
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
    control.13 {
        iface MIXER
        name 'Mux Capture Volume'
        index 1
        value.0 1
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3000
            dbvalue.0 1000
            dbvalue.1 0
        }
    }
    control.14 {
        iface MIXER
        name 'IEC958 Playback Source'
        value 'Digital Playback'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 'Digital Playback'
            item.1 'Analog Mux 1'
            item.2 'Analog Mux 2'
        }
    }
    control.15 {
        iface MIXER
        name 'Master Playback Volume'
        value 64
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 64'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
        }
    }
    control.16 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.17 {
        iface MIXER
        name 'Mute-LED Mode'
        value 'Follow Master'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Off
            item.1 On
            item.2 'Follow Master'
        }
    }
    control.18 {
        iface CARD
        name 'Speaker Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.19 {
        iface CARD
        name 'Front Headphone Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.20 {
        iface CARD
        name 'Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.21 {
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
state.HDMI {
    control.1 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
btrfs
zlib_deflate
libcrc32c
ufs
qnx4
hfsplus
hfs
minix
ntfs
msdos
jfs
xfs
reiserfs
ext2
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_seq_device
nls_iso8859_1
snd_hda_codec_hdmi
parport_pc
ppdev
bnep
rfcomm
bluetooth
kvm
hp_wmi
sparse_keymap
snd_hda_codec_idt
microcode
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
psmouse
sp5100_tco
serio_raw
i2c_piix4
k10temp
snd_timer
radeon
snd
uvcvideo
videobuf2_core
videodev
videobuf2_vmalloc
videobuf2_memops
ttm
drm_kms_helper
drm
soundcore
snd_page_alloc
i2c_algo_bit
b43
mac80211
cfg80211
jmb38x_ms
wmi
bcma
shpchp
memstick
joydev
ir_lirc_codec
lirc_dev
ir_mce_kbd_decoder
ir_sanyo_decoder
ir_sony_decoder
ir_jvc_decoder
ir_rc6_decoder
ir_rc5_decoder
ir_nec_decoder
video
rc_rc6_mce
hp_accel
lis3lv02d
input_polldev
ene_ir
rc_core
mac_hid
lp
parport
hid_generic
usbhid
hid
pata_atiixp
ssb
r8169
sdhci_pci
sdhci
usb_storage


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0a 0x02214010
0x0b 0x02a19020
0x0c 0x40f100f0
0x0d 0x40f100f1
0x0e 0x40f100f2
0x0f 0x40f100f3
0x14 0x40f100f4
0x18 0x40f100f5
0x19 0x40f100f6
0x1e 0x40f100f7
0x1f 0x40f100f8
0x20 0x40f100f9
0x27 0x40f100fa

/sys/class/sound/hwC0D0/driver_pin_configs:
0x0d 0x90170010

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:


!!ALSA/HDA dmesg
!!--------------

[   18.962856] sp5100_tco: mmio address 0xfec000f0 already in use
[   19.007049] snd_hda_intel 0000:00:14.2: >setting latency timer to 64
[   19.025134] microcode: CPU0: patch_level=0x02000057
[   19.100930] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   19.101022] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   19.304922] cfg80211: World regulatory domain updated:
--
[   21.483191] [drm] Connector 1:
[   21.483192] [drm]   HDMI-A-1
[   21.483194] [drm]   HPD1
--
[   22.491336] [drm] Initialized radeon 2.18.0 20080528 for 0000:01:05.0 on minor 0
[   22.491446] snd_hda_intel 0000:01:05.1: >setting latency timer to 64
[   23.647073] r8169 0000:0a:00.0: >eth0: link up

```

---

### Post by srekcahrai on 2013-01-29
After many months I have finally found the solution for microphone in HP Pavilion DV4.
The solution is:
1. Open /etc/modprobe.d/alsa-base file, if not found /etc/modprobe.d/alsa-base.conf file using gedit.
2. Add these lines:
```

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp=dv4 
options snd-hda-intel enable_msi=1

```
3. Reboot

---

### Post by Yellow Pasque on 2013-01-29
I'm not sure why that works, since hp-dv4 is not a valid model (and your syntax is incorrect anyway).
```
STAC92HD71B*/75B*
============
  ref		Reference board
  hp-m4		HP mini 1000
  hp-dv5	HP dv series
  hp-hdx	HP HDX series
  hp-dv4-1222nr	HP dv4-1222nr (with LED support)
  auto		BIOS setup (default)
```

---

### Post by srekcahrai on 2013-01-29
Might be I have no idea about audio. Can you tell me how did you learn to troubleshoot Ubuntu? Did you take some lessons or are there good books out there in market?

---

### Post by freefixkorma on 2013-03-06
it does not work for me any ideas i still missing microphone on alsamixer panel will appreciate thanks 
freefix

---

### Post by freefixkorma on 2013-03-06
i am still like this[ATTACH=CONFIG]239857[/ATTACH]microphone missing any ideas will appreciate i understand this thread is solve but anyone can add to my issue i will appreciate

---

