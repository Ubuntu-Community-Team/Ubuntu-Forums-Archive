---
title: "HDMI Sound help"
date: 2013-02-08
forum: Hardware
---

### Post by mdew on 2013-02-08
I've tried various combinations in alsa-base.conf (below) to get the audio to work through HDMI->Sony TV

aplay/mplayer shows no sound, and alsamixer isn't muting it.

The card is a Geforce 210 (1G). 

Anyone got any pointers in making the audio work via hdmi? I've followed this [http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_HDMI_audio_on_GeForce_GT210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_HDMI_audio_on_GeForce_GT210,_GT220,_or_GT240) without success..

```

root@mediabawx:~# cat /etc/modprobe.d/alsa-base.conf | grep intel
options snd-intel8x0m index=-2
#options snd-hda-intel enable_msi=0 probe_mask=0xfff2
#options snd-hda-intel enable_msi=0 index=-2
# options snd-hda-intel enable_msi=0 index=1
# no work options snd-hda-intel
# no work options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
options snd-hda-intel enable_msi=0
#options snd-hda-intel probe_mask=2

```

```

root@mediabawx:~# cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcffc000 irq 16
 1 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xf7000000
root@mediabawx:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

root@mediabawx:~# aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversion

root@mediabawx:~# cat /etc/asound.conf
pcm.!default hdmi:NVidia
pcm:iec958 hdmi:NVidia

The following plays no sound.
root@mediabawx:~# aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
root@mediabawx:~# aplay -D plughw:0,7 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
root@mediabawx:~# aplay -D plughw:0,8 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
root@mediabawx:~# aplay -D plughw:0,9 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

root@mediabawx:~# cat /proc/asound/pcm
00-03: HDMI 0 : HDMI 0 : playback 1
00-07: HDMI 0 : HDMI 0 : playback 1
00-08: HDMI 0 : HDMI 0 : playback 1
00-09: HDMI 0 : HDMI 0 : playback 1
01-00: CX88 Digital : CX88 Digital : capture 1

root@mediabawx:~# lspci
00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: NVIDIA Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:07.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
03:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
03:09.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)

root@mediabawx:~# lsmod | grep hdmi
snd_hda_codec_hdmi     32049  4
snd_hda_codec         134213  2 snd_hda_codec_hdmi,snd_hda_intel
snd_pcm                96668  6 snd_hda_codec_hdmi,snd_soc_wm8776,snd_soc_core,snd_hda_intel,snd_hda_codec,cx88_alsa
snd                    78921  11 snd_hda_codec_hdmi,snd_soc_core,snd_hda_intel,snd_hda_codec,snd_hwdep,cx88_alsa,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

root@mediabawx:~# cat /proc/asound/card0/codec#3
Codec: Nvidia GPU 0b HDMI/DP
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de000b
Subsystem Id: 0x10de0101
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Converter: stream=6, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="HDMI/DP,pcm=9 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=3, device=0
  Control: name="IEC958 Playback Pro Mask", index=3, device=0
  Control: name="IEC958 Playback Default", index=3, device=0
  Control: name="IEC958 Playback Switch", index=3, device=0
  Control: name="ELD", index=0, device=9
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x04

```

---

