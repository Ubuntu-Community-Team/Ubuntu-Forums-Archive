---
title: "IBM X41 (not tablet) no sound"
date: 2009-05-14
forum: Hardware
---

### Post by frcsyk on 2009-05-14
Hello!

I installed Ubuntu 9.04 on my laptop and everything works fine except for my sound card.  I ran through the troubleshooting steps but came up short and am still without sound.  I posted my ALSA information below.  Thanks in advance for your help! 

!!################################
!!ALSA Information Script v 0.4.56
!!################################

!!Script ran on: Thu May 14 12:46:10 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!Kernel Information
!!------------------

Kernel release:    2.6.28-11-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.18rc3
Library version:    1.0.18
Utilities version:  1.0.18


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


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

 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1981B at irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1e.2 0401: 8086:266e (rev 03)
    Subsystem: 1014:0581


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
ac97_clock : 0
ac97_quirk : <NULL>
buggy_irq : N
buggy_semaphore : N
enable : N
id : <NULL>
index : -1
joystick : 0
spdif_aclink : 0
xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1981B

PCI Subsys Vendor: 0x1014
PCI Subsys Device: 0x0581

Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         :  0dB [ 0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 VRA
Extended status  : VRA
PCM front DAC    : 8000Hz
PCM ADC          : 44100Hz



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0090
0:02 = 0000
0:04 = 0606
0:06 = 0006
0:08 = 0000
0:0a = 0000
0:0c = 801f
0:0e = 801f
0:10 = 1f1f
0:12 = 0606
0:14 = 0000
0:16 = 9f9f
0:18 = 0606
0:1a = 0000
0:1c = 0000
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0601
0:2a = 0031
0:2c = 1f40
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2000
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 4000
0:5e = 0000
0:60 = 8080
0:62 = 0000
0:64 = 8000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 0008
0:74 = 1001
0:76 = 2010
0:78 = 0000
0:7a = 0000
0:7c = 4144
0:7e = 5374
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 10 May 14 20:27 /dev/snd/controlC0
crw-rw----  1 root audio 116,  9 May 14 20:28 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  8 May 14 21:09 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  7 May 14 20:27 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116,  6 May 14 20:27 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116,  5 May 14 20:27 /dev/snd/pcmC0D3c
crw-rw----  1 root audio 116,  4 May 14 21:10 /dev/snd/pcmC0D4p
crw-rw----  1 root audio 116,  3 May 14 20:27 /dev/snd/seq
crw-rw----  1 root audio 116,  2 May 14 20:27 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [ICH6]

Card hw:0 'ICH6'/'Intel ICH6 with AD1981B at irq 22'
  Mixer name    : 'Analog Devices AD1981B'
  Components    : 'AC97a:41445374'
  Controls      : 26
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [-9.00dB] [on]
  Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [on] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost ( 20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.ICH6 {
    control.1 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Master Playback Switch'
        value.0 true
        value.1 true
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 31
        value.1 31
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
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 25
        value.1 25
    }
    control.5 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Mono Playback Switch'
        value true
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Mono Playback Volume'
        value 25
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Phone Playback Switch'
        value false
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Phone Playback Volume'
        value 0
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Playback Switch'
        value false
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value 0
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Boost ( 20dB)'
        value false
    }
    control.12 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Line Playback Switch'
        value.0 true
        value.1 true
    }
    control.13 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'CD Playback Switch'
        value.0 true
        value.1 true
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'CD Playback Volume'
        value.0 25
        value.1 25
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Aux Playback Switch'
        value.0 false
        value.1 false
    }
    control.17 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Aux Playback Volume'
        value.0 0
        value.1 0
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'PCM Playback Switch'
        value.0 true
        value.1 true
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'PCM Playback Volume'
        value.0 25
        value.1 25
    }
    control.20 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 2
        comment.item.0 Mic
        comment.item.1 CD
        comment.item.2 Video
        comment.item.3 Aux
        comment.item.4 Line
        comment.item.5 Mix
        comment.item.6 'Mix Mono'
        comment.item.7 Phone
        iface MIXER
        name 'Capture Source'
        value.0 Mic
        value.1 Mic
    }
    control.21 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
    }
    control.22 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 15'
        comment.dbmin 0
        comment.dbmax 2250
        iface MIXER
        name 'Capture Volume'
        value.0 0
        value.1 0
    }
    control.23 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mix
        comment.item.1 Mic
        iface MIXER
        name 'Mono Output Select'
        value Mix
    }
    control.24 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic1
        comment.item.1 Mic2
        iface MIXER
        name 'Mic Select'
        value Mic1
    }
    control.25 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Stereo Mic'
        value false
    }
    control.26 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'External Amplifier'
        value true
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
michael_mic
arc4
ecb
ieee80211_crypt_tkip
i915
drm
binfmt_misc
ppdev
bridge
stp
bnep
input_polldev
lp
parport
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
iTCO_wdt
snd_seq
snd_timer
snd_seq_device
pcmcia
iTCO_vendor_support
thinkpad_acpi
psmouse
led_class
intel_agp
snd
serio_raw
yenta_socket
rsrc_nonstatic
sdhci_pci
sdhci
nvram
video
pcspkr
agpgart
ipw2200
soundcore
snd_page_alloc
nsc_ircc
pcmcia_core
output
ieee80211
ieee80211_crypt
irda
crc_ccitt
tg3
fbcon
tileblit
font
bitblit
softcursor

---

### Post by frcsyk on 2009-05-16
I'm still having trouble with this.  If I launch the Pulseaudio Applet and play a video then chose Volume meter playback I can see that sound is play but I still can't hear anything.  

I've spent hours browsing the forums but I still can't resolve this.  Anyone have any ideas?

---

