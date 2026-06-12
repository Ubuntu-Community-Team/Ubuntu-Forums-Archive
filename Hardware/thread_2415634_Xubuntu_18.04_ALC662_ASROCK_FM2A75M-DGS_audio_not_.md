---
title: "Xubuntu 18.04 ALC662 ASROCK FM2A75M-DGS audio not working"
date: 2019-03-29
forum: Hardware
---

### Post by nlona on 2019-03-29
Huge problem no audio even inserting each by each following options [https://www.kernel.org/doc/html/v4.15/sound/hd-audio/models.html#alc66x-67x-892](https://www.kernel.org/doc/html/v4.15/sound/hd-audio/models.html#alc66x-67x-892)

```
hp@hp-desktop:~$ lsb_release && uname -a && cat /proc/asound/cards && aplay -l && lspci -nnk |grep -iA2 audio && ps -C esd && ps -C arts && ps -C pulseaudio
No LSB modules are available.
Linux hp-desktop 4.15.0-46-generic #49-Ubuntu SMP Wed Feb 6 09:33:07 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe100000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe080000 irq 19
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Generic [HD-Audio Generic], dispositivo 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 7: HDMI 1 [HDMI 1]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 8: HDMI 2 [HDMI 2]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
    Subsystem: ASRock Incorporation FCH Azalia Controller [1849:7662]
    Kernel driver in use: snd_hda_intel
--
01:00.1 Audio device [0403]: NVIDIA Corporation GP107GL High Definition Audio Controller [10de:0fb9] (rev a1)
    Subsystem: eVga.com. Corp. GP107GL High Definition Audio Controller [3842:6251]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
  PID TTY          TIME CMD
hp@hp-desktop:~$cat  /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

[COLOR=#ff0000]Tried all these options 1by1 obviously without #[/COLOR]
#options snd_hda_intel model=generic
#options snd_hda_intel model=auto
#options snd_hda_intel model=alc662-headset
#options snd_hda_intel model=asrock-mobo
#options snd_hda_intel model=laptop
#options snd_hda_intel model=3stack-6ch
#options snd_hda_intel model=3stack-6ch-dig
#options snd-hda-intel power_save=10 power_save_controller=N
#options snd-hda-intel model=mario
#    Chromebook mario model fixup
#options snd-hda-intel model=asus-mode1
#    ASUS
#options snd-hda-intel model=asus-mode2
#   ASUS
#options snd-hda-intel model=asus-mode3
#   ASUS
#options snd-hda-intel model=asus-mode4
#    ASUS
#options snd-hda-intel modelasus-mode5
#    ASUS
#options snd-hda-intel model=asus-mode6
#    ASUS
#options snd-hda-intel model=asus-mode7
#    ASUS
#options snd-hda-intel model=asus-mode8
#   ASUS
#options snd-hda-intel model=inv-dmic
#    Inverted internal mic workaround
#options snd-hda-intel model=dell-headset-multi
#    Headset jack, which can also be used as mic-in
#options snd-hda-intel model=dual-codecs
#options snd-hda-intel patch=on-board-patch,hdmi-patch
#options snd-hda-intel model=intel-alc662
#options snd-hda-intel model=intel-alc662 position_fix=1
#options snd-hda-intel model=intel-alc889a position_fix=1
#options snd-hda-intel id=PCH,HDMI index=0,1

#options snd-hda-intel model=minimal
#options snd-hda-intel model=gpio1
#options snd-hda-intel model=laptop-amic
#options snd-hda-intel model=laptop-dmic
#options snd-hda-intel model=alc283-sense-combo
#options snd-hda-intel model=alc700-ref
#options snd-hda-intel model=acer-aspire
#options snd-hda-intel model=
#options snd-hda-intel model=
#options snd-hda-intel model=


#options snd-hda-intel model=mmin_fp




```
None worked
```
hp@hp-desktop:~$ amixer -c0
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
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
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [33.00dB] [on]
  Front Right: Capture 31 [100%] [33.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [33.00dB] [off]
  Front Right: Capture 31 [100%] [33.00dB] [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '6ch'
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Loopback Mixing',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
hp@hp-desktop:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Generic
    HD-Audio Generic, ALC662 rev1 Analog
    Default Audio Device
front:CARD=Generic,DEV=0
    HD-Audio Generic, ALC662 rev1 Analog
    Front speakers
surround21:CARD=Generic,DEV=0
    HD-Audio Generic, ALC662 rev1 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Generic,DEV=0
    HD-Audio Generic, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Generic,DEV=0
    HD-Audio Generic, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Generic,DEV=0
    HD-Audio Generic, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Generic,DEV=0
    HD-Audio Generic, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Generic,DEV=0
    HD-Audio Generic, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Generic,DEV=0
    HD-Audio Generic, ALC662 rev1 Analog
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=0
    HD-Audio Generic, ALC662 rev1 Analog
    Direct sample snooping device
hw:CARD=Generic,DEV=0
    HD-Audio Generic, ALC662 rev1 Analog
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=0
    HD-Audio Generic, ALC662 rev1 Analog
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 1
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 2
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Hardware device with all software conversions


```
[https://pastebin.com/D5qitX8s](https://pastebin.com/D5qitX8s)
[https://imgur.com/a/UluneZU](https://imgur.com/a/UluneZU)
[https://streamable.com/kv85z](https://streamable.com/kv85z)


No timidity package is installed

---

