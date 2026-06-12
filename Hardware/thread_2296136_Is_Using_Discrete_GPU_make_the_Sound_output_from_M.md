---
title: "Is Using Discrete GPU make the Sound output from Motherboard Disappear?"
date: 2015-09-23
forum: Hardware
---

### Post by YLTO on 2015-09-23
So I just have bought a brand new AMD R9 380 for my PC. I've installed fglrx and catalyst control center. The only sound come out is from My Monitor's audio jack, the sound quality is pretty bad though. My speaker connected to the motherboard "line out" audio jack does not output any sound at all. I've followed [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) without any success. Could you please help me out? and why the sound output show only hdmi/displayport, why my audio output from motherboard not listed?

Below is some info for troubleshooting

```


[IMG]http://i.imgur.com/mEKO2bm.png[/IMG]


upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Wed Sep 23 20:03:14 UTC 2015




!!Linux Distribution
!!------------------


Ubuntu 15.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 15.04" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 15.04" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"




!!DMI Information
!!---------------


Manufacturer:      MSI
Product Name:      MS-7971
Product Version:   2.0
Firmware Version:  A.20




!!Kernel Information
!!------------------


Kernel release:    3.19.0-28-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     k3.19.0-28-generic
Library version:    1.0.28
Utilities version:  1.0.28




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


 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xdfd60000 irq 132




!!PCI Soundcards installed in the system
!!--------------------------------------


00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aad8




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:1f.3 0403: 8086:a170 (rev 31)
    Subsystem: 1462:f971
--
01:00.1 0403: 1002:aad8
    Subsystem: 1787:aad8




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
snd_hda_intel: model=generic




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
    model : generic,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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


Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100700
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=1, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  IEC Coding Type: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02
Node 0x04 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="HDMI/DP,pcm=7 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Control: name="ELD", index=0, device=7
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=02, enabled=1
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="HDMI/DP,pcm=8 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Control: name="ELD", index=0, device=8
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="HDMI/DP,pcm=9 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=3, device=0
  Control: name="IEC958 Playback Pro Mask", index=3, device=0
  Control: name="IEC958 Playback Default", index=3, device=0
  Control: name="IEC958 Playback Switch", index=3, device=0
  Control: name="ELD", index=0, device=9
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=04, enabled=1
  Connection: 1
     0x08
Node 0x0a [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x0b [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="HDMI/DP,pcm=10 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=4, device=0
  Control: name="IEC958 Playback Pro Mask", index=4, device=0
  Control: name="IEC958 Playback Default", index=4, device=0
  Control: name="IEC958 Playback Switch", index=4, device=0
  Control: name="ELD", index=0, device=10
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x0a
Node 0x0c [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x0d [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="HDMI/DP,pcm=11 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=5, device=0
  Control: name="IEC958 Playback Pro Mask", index=5, device=0
  Control: name="IEC958 Playback Default", index=5, device=0
  Control: name="IEC958 Playback Switch", index=5, device=0
  Control: name="ELD", index=0, device=11
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=06, enabled=1
  Connection: 1
     0x0c
Node 0x0e [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x0f [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0e
--endcollapse--




!!ALSA Device nodes
!!-----------------


crw-rw----+ 1 root audio 116,  2 Sep 25  2015 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  9 Sep 25  2015 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  7 Sep 25  2015 /dev/snd/pcmC1D10p
crw-rw----+ 1 root audio 116,  8 Sep 25  2015 /dev/snd/pcmC1D11p
crw-rw----+ 1 root audio 116,  3 Sep 24 02:33 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116,  4 Sep 25  2015 /dev/snd/pcmC1D7p
crw-rw----+ 1 root audio 116,  5 Sep 25  2015 /dev/snd/pcmC1D8p
crw-rw----+ 1 root audio 116,  6 Sep 25  2015 /dev/snd/pcmC1D9p
crw-rw----+ 1 root audio 116,  1 Sep 25  2015 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Sep 25  2015 /dev/snd/timer


/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Sep 25  2015 .
drwxr-xr-x 3 root root 260 Sep 25  2015 ..
lrwxrwxrwx 1 root root  12 Sep 25  2015 pci-0000:01:00.1 -> ../controlC1




!!Aplay/Arecord output
!!--------------------


APLAY


**** List of PLAYBACK Hardware Devices ****
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ARECORD


**** List of CAPTURE Hardware Devices ****


!!Amixer output
!!-------------


!!-------Mixer controls for card 1 [Generic]


Card hw:1 'Generic'/'HD-Audio Generic at 0xdfd60000 irq 132'
  Mixer name    : 'ATI R6xx HDMI'
  Components    : 'HDA:1002aa01,00aa0100,00100700'
  Controls      : 42
  Simple ctrls  : 6
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
Simple mixer control 'IEC958',4
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',5
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]




!!Alsactl output
!!--------------


--startcollapse--
state.Generic {
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
        value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
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
        value '100009000e10000105000000000100001e6db85a4c47204950532046554c4c484400090707000000'
        comment {
            access 'read volatile'
            type BYTES
            count 40
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
        iface CARD
        name 'HDMI/DP,pcm=10 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.26 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 4
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.27 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 4
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.28 {
        iface MIXER
        name 'IEC958 Playback Default'
        index 4
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.29 {
        iface MIXER
        name 'IEC958 Playback Switch'
        index 4
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.30 {
        iface PCM
        device 10
        name ELD
        value ''
        comment {
            access 'read volatile'
            type BYTES
            count 0
        }
    }
    control.31 {
        iface CARD
        name 'HDMI/DP,pcm=11 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.32 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 5
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
        index 5
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
        index 5
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.35 {
        iface MIXER
        name 'IEC958 Playback Switch'
        index 5
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.36 {
        iface PCM
        device 11
        name ELD
        value ''
        comment {
            access 'read volatile'
            type BYTES
            count 0
        }
    }
    control.37 {
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
    control.38 {
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
    control.39 {
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
    control.40 {
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
    control.41 {
        iface PCM
        device 10
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
    control.42 {
        iface PCM
        device 11
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
uas
usb_storage
ctr
ccm
nls_iso8859_1
arc4
xhci_plat_hcd
dwc3
udc_core
mxm_wmi
phy_generic
ath9k
ath9k_common
ath9k_hw
ath
mac80211
x86_pkg_temp_thermal
coretemp
kvm_intel
kvm
crct10dif_pclmul
joydev
crc32_pclmul
ghash_clmulni_intel
cfg80211
aesni_intel
aes_x86_64
lrw
gf128mul
glue_helper
ablk_helper
cryptd
serio_raw
i2c_hid
fglrx
8250_fintek
wmi
mac_hid
acpi_pad
i915_bpo
intel_ips
video
drm_kms_helper
snd_hda_codec_hdmi
drm
i2c_algo_bit
snd_hda_intel
snd_hda_controller
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
snd_seq
snd_seq_device
snd_timer
snd
amd_iommu_v2
soundcore
shpchp
dwc3_pci
parport_pc
ppdev
lp
parport
autofs4
hid_generic
usbhid
hid
psmouse
r8169
mii
ahci
libahci




!!Sysfs Files
!!-----------


/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x185600f0
0x05 0x185600f0
0x07 0x185600f0
0x09 0x185600f0
0x0b 0x185600f0
0x0d 0x185600f0
0x0f 0x585600f0


/sys/class/sound/hwC1D0/driver_pin_configs:


/sys/class/sound/hwC1D0/user_pin_configs:


/sys/class/sound/hwC1D0/init_verbs:


/sys/class/sound/hwC1D0/hints:




!!ALSA/HDA dmesg
!!--------------


[    1.957920] AMD IOMMUv2 functionality not available on this system
[    1.988564] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    1.988681] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    1.994803] [drm] Initialized drm 1.1.0 20060810
[    1.997507] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[    1.997590] input: HD-Audio Generic HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[    1.998369] input: HD-Audio Generic HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[    1.998434] input: HD-Audio Generic HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[    1.998523] input: HD-Audio Generic HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    1.998626] input: HD-Audio Generic HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[    2.010300] snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)
[    2.024916] wmi: Mapper loaded


```

---

### Post by grahammechanical on 2015-09-23
Would you please enclose all that information in quote tags then I will not need to scroll the web page down into the Earth's crust to get to the reply box.

My computer is connected to a digital TV as a monitor using the HMDI connections on the graphic adapter and the TV. Sound as well as video is played through the HDMI connection to the TV's speakers, For this reason Sound Settings>Output does not give me an option to switch the output to the motherboard line out/headphone socket. But once I plug in a set of headphones or any appropriate cable with a headphone jack on it, then Sound Settings>Output gives me the option to select Headphones>Built in Audio and change the source of the output.

Regards

---

### Post by Yellow Pasque on 2015-09-23
In the future, please use **code** (not quote) tags for such large blocks of output.

>  snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)
Z170 chipset motherboards exhibit this issue on Ubuntu 15.04. The solution is to upgrade the sound module/driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

> snd_hda_intel: model=generic
Get rid of this line. You don't need it and it may cause issues.

---

### Post by YLTO on 2015-09-24
> **Temüjin said:**
> In the future, please use **code** (not quote) tags for such large blocks of output.


Z170 chipset motherboards exhibit this issue on Ubuntu 15.04. The solution is to upgrade the sound module/driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)


Get rid of this line. You don't need it and it may cause issues.


wow. it worked! Thanks a lot. You saved my life. :p

> **Temüjin said:**
> In the future, please use **code** (not quote) tags for such large blocks of output.

okay. I've changed it.

---

