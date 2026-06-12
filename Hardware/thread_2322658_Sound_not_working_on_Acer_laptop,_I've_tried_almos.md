---
title: "Sound not working on Acer laptop, I've tried almos everything."
date: 2016-04-29
forum: Hardware
---

### Post by Vctor_Vanda on 2016-04-29
Hi, I think I've tried everything to solve this problem. I have an old laptop (Acer One ZG5). I installed Ubuntu server. The idea is use this lap as an audio player, keep it plugged to a speakers and control it through an android shh remote application. 

The problem is that I can't hear any sound on the speakers. 

[SIZE=4]I've tried [/SIZE]
[B]
1[/B]. Installed alsa

**2**. Installed drivers for my soud, (Codec: Realtek ALC268)
```
acer@ubuntu:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
acer@ubuntu:~$
```
```
acer@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

**3**. Reloaded alsa 
```
sudo alsa force-reload
```

**4**. Iv'e rebooted

**5**. All levels on alsamixer are up. 
[IMG]blob:https://drive.google.com/f791d358-6d8a-48e3-a453-eb6c2c62548e[/IMG]

**TESTS**


Tested with **speaker-test** It keeps looping without sound: 
```
acer@ubuntu:~/audio/Beatles/w$ speaker-test

speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 10.986026
 0 - Front Left
Time per period = 10.990444
 0 - Front Left
Time per period = 10.991064
 0 - Front Left
Time per period = 10.989458
 0 - Front Left
Time per period = 10.990358
 0 - Front Left
Time per period = 10.989332
 0 - Front Left
Time per period = 10.990805
 0 - Front Left
Time per period = 10.990377
 0 - Front Left
Time per period = 10.990152
 0 - Front Left
Time per period = 10.990724
 0 - Front Left
Time per period = 10.990570
 0 - Front Left
Time per period = 10.990115
 0 - Front Left
Time per period = 10.990063
 0 - Front Left
Time per period = 10.991501
 0 - Front Left
Time per period = 10.989703
 0 - Front Left
Time per period = 10.990047
 0 - Front Left
Time per period = 10.990678
 0 - Front Left
Time per period = 10.990887
 0 - Front Left
Time per period = 10.990925
 0 - Front Left
Time per period = 10.988010
 0 - Front Left
Time per period = 10.991646
 0 - Front Left
Time per period = 10.990635
 0 - Front Left
Time per period = 10.990617
 0 - Front Left
^Z
[6]+  Stopped                 speaker-test


```

- If I play a file with **aplay**, it appears to be playing, but can't hear anything:
```
acer@ubuntu:~/audio/Beatles/w$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono


```

- Same Happens with **mplayer**: 
```
acer@ubuntu:~/audio/Beatles/w$ mplayer *
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [1] - 07 - While My Guitar Gently Weeps.mp3.
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
Audio only file format detected.
Clip info:
 Title: [1] - 07 - While My Guitar Ge
 Artist: The Beatles
 Album: The Beatles (White Album)
 Year:
 Comment:
 Genre: Other
Load subtitles in ./
==========================================================================
Trying to force audio codec driver family mp3lib...
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 320.0 kbit/22.68% (ratio: 40000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  17.9 (17.9) of 284.0 (04:44.0)  2.7%

```

I also ran diagnostic: 
```
bash alsa-info.sh --stdout
```

The result showed on "!!-------Mixer controls for card 0 [Intel]" is that everything is in [off] status, how can I change it to [on]
```
acer@ubuntu:~/audio/Beatles/w$ bash alsa-info.sh --stdout
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Fri Apr 29 17:42:10 UTC 2016


!!Linux Distribution
!!------------------

Ubuntu 12.04.5 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.5 LTS)"


!!DMI Information
!!---------------

Manufacturer:      Acer
Product Name:      AOA150
Product Version:   1
Firmware Version:  v0.3310


!!Kernel Information
!!------------------

Kernel release:    3.13.0-85-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.13.0-85-generic
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x78540000 irq 45


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
        Subsystem: 1025:015b


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
snd-hda-intel: model=acer-aspire


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
        model : acer-aspire,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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

Codec: Realtek ALC268
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0268
Subsystem Id: 0x1025015b
Revision Id: 0x100101
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC268 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
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
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x100111: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x100111: Stereo
  Device: name="ALC268 Analog", type="Audio", device=0
  Converter: stream=4, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0e [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00]
  Connection: 1
     0x02
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x02 0x1d
Node 0x10 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80]
  Connection: 3
     0x03 0x1d 0x02
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Control: name="Internal Mic Phantom Jack", index=0, device=0
  Pincap 0x00000020: IN
  Pin Default 0x99a30920: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x13 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Speaker Phantom Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0f
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0321401f: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x10
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x02 0x02]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x03a19830: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=02, enabled=1
  Connection: 1
     0x02
Node 0x19 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Node 0x1b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Pincap 0x00000020: IN
  Pin Default 0x4015812d: [N/A] Speaker at Ext N/A
    Conn = Optical, Color = Purple
    DefAssociation = 0x2, Sequence = 0xd
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000010: OUT
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
  Processing caps: benign=0, ncoeff=10
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x23 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x0a, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x9d 0x9d]
  Connection: 7
     0x18 0x19 0x1a 0x1c 0x14 0x15 0x12*
Node 0x24 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x0a, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x01 0x01]
  Connection: 7
     0x18 0x19 0x1a 0x1c 0x14* 0x15 0x13
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T 1 root audio 116,  5 Apr 29 09:33 /dev/snd/controlC0
crw-rw---T 1 root audio 116,  4 Apr 29 09:33 /dev/snd/hwC0D0
crw-rw---T 1 root audio 116,  3 Apr 29 09:35 /dev/snd/pcmC0D0c
crw-rw---T 1 root audio 116,  2 Apr 29 12:33 /dev/snd/pcmC0D0p
crw-rw---T 1 root audio 116,  1 Apr 29 12:31 /dev/snd/seq
crw-rw---T 1 root audio 116, 33 Apr 29 09:33 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Apr 29 09:33 .
drwxr-xr-x 3 root root 180 Apr 29 09:33 ..
lrwxrwxrwx 1 root root  12 Apr 29 09:33 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0x78540000 irq 45'
  Mixer name    : 'Realtek ALC268'
  Components    : 'HDA:10ec0268,1025015b,00100101'
  Controls      : 20
  Simple ctrls  : 9
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [off]
  Front Right: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [off]
  Front Right: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 2 [100%] [40.00dB]
  Front Right: 2 [100%] [40.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 12
  Mono:
  Front Left: Playback 12 [100%] [0.00dB] [off]
  Front Right: Playback 12 [100%] [0.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 29 [94%] [28.50dB] [off]
  Front Right: Capture 29 [94%] [28.50dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Inverted Internal Mic',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [on]


!!Alsactl output
!!--------------

--startcollapse--
state.Intel {
        control.1 {
                iface MIXER
                name 'Headphone Playback Volume'
                value.0 64
                value.1 64
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 64'
                        dbmin -6400
                        dbmax 0
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.2 {
                iface MIXER
                name 'Headphone Playback Switch'
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
                name 'Speaker Playback Volume'
                value.0 64
                value.1 64
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 64'
                        dbmin -6400
                        dbmax 0
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.4 {
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
        control.5 {
                iface MIXER
                name 'Auto-Mute Mode'
                value Disabled
                comment {
                        access 'read write'
                        type ENUMERATED
                        count 1
                        item.0 Disabled
                        item.1 Enabled
                }
        }
        control.6 {
                iface MIXER
                name 'Capture Volume'
                value.0 29
                value.1 29
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 31'
                        dbmin -1500
                        dbmax 3150
                        dbvalue.0 2850
                        dbvalue.1 2850
                }
        }
        control.7 {
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
        control.8 {
                iface MIXER
                name 'Mic Boost Volume'
                value.0 2
                value.1 2
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 2'
                        dbmin 0
                        dbmax 4000
                        dbvalue.0 4000
                        dbvalue.1 4000
                }
        }
        control.9 {
                iface MIXER
                name 'Inverted Internal Mic Capture Switch'
                value true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 1
                }
        }
        control.10 {
                iface MIXER
                name 'Master Playback Volume'
                value 64
                comment {
                        access 'read write'
                        type INTEGER
                        count 1
                        range '0 - 64'
                        dbmin -6400
                        dbmax 0
                        dbvalue.0 0
                }
        }
        control.11 {
                iface MIXER
                name 'Master Playback Switch'
                value false
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 1
                }
        }
        control.12 {
                iface CARD
                name 'Mic Jack'
                value false
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.13 {
                iface CARD
                name 'Internal Mic Phantom Jack'
                value true
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.14 {
                iface CARD
                name 'Headphone Jack'
                value true
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.15 {
                iface CARD
                name 'Speaker Phantom Jack'
                value true
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.16 {
                iface MIXER
                name 'Beep Playback Volume'
                value.0 12
                value.1 12
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 12'
                        dbmin -2400
                        dbmax 0
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.17 {
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
        control.18 {
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
        control.19 {
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
        control.20 {
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
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_seq_device
dm_crypt
arc4
joydev
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
ath5k
snd_hwdep
snd_pcm
ath
mac80211
uvcvideo
psmouse
videobuf2_core
videodev
sparse_keymap
acerhdf
serio_raw
snd_timer
coretemp
videobuf2_vmalloc
cfg80211
videobuf2_memops
snd
jmb38x_ms
lpc_ich
memstick
soundcore
snd_page_alloc
shpchp
mac_hid
lp
parport
i915
pata_acpi
r8169
drm_kms_helper
sdhci_pci
sdhci
mii
drm
i2c_algo_bit
video
wmi


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x12 0x99a30920
0x13 0x411111f0
0x14 0x99130110
0x15 0x0321401f
0x16 0x411111f0
0x18 0x03a19830
0x19 0x411111f0
0x1a 0x411111f0
0x1c 0x411111f0
0x1d 0x4015812d
0x1e 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:


!!ALSA/HDA dmesg
!!--------------

[   20.029865] type=1400 audit(1461940406.952:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=671 comm="apparmor_parser"
[   20.146916] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   20.312342] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
--
[   20.312385] realtek: Enabling init ASM_ID=0x812d CODEC_ID=10ec0268
[   20.320532] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   20.321307] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   20.507890] psmouse serio2: synaptics: queried max coordinates: x [..5888], y [..5218]


```


This computer used to have windows and sound was playing normal, any ideas of what should I be missing?

---

### Post by Vctor_Vanda on 2016-04-29
I Solved the problem, 

After running 
```
amixer
```

```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [off]
  Front Right: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [off]
  Front Right: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 2 [100%] [40.00dB]
  Front Right: 2 [100%] [40.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 12
  Mono:
  Front Left: Playback 12 [100%] [0.00dB] [off]
  Front Right: Playback 12 [100%] [0.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 29 [94%] [28.50dB] [off]
  Front Right: Capture 29 [94%] [28.50dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Inverted Internal Mic',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [on]

I umuted each mixer:

[CODE]amixer sset Headphone unmute
amixer sset Master unmute
amixer sset Speaker unmute
```

That was it... Sount tested and working. 

```
acer@ubuntu:/etc/modprobe.d$ amixer
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
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 2 [100%] [40.00dB]
  Front Right: 2 [100%] [40.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 12
  Mono:
  Front Left: Playback 12 [100%] [0.00dB] [off]
  Front Right: Playback 12 [100%] [0.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 29 [94%] [28.50dB] [off]
  Front Right: Capture 29 [94%] [28.50dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Inverted Internal Mic',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [on]
```

---

### Post by mickee384 on 2016-04-29
does it retain the settings after a reboot?

---

