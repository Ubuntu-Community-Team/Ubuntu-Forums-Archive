---
title: "Intel using VAAPI HDMI 7.1 surround problems"
date: 2015-05-28
forum: Hardware
---

### Post by afremont on 2015-05-28
I'm running Mythbuntu, but this smells more like a generic ALSA issue.  Please move it if this isn't the appropriate forum.

I'm having somewhat of a problem with this setup.  After a bunch of tinkering, I'm able to get the receiver to output 7.1 surround sound mostly correctly.  The oddity is when I test the sound using Mythfrontend->Setup->Audio etc it connects as PCM Multichannel (as designed I think) and outputs sound on all the speakers, just with the wrong mapping.  When I watch Live TV (haven't tested anything else yet), it connects as Dolby Ex (receiver Display shows a 5.1 to 7.1 conversion, and that seems right) and the sound seems to play from the correct speakers.  I believe that passthru is working in this case as the receiver indicates an incoming DD 5.1 signal.


My motherboard is a Gigabyte GA-H97M-D3H.  I'm using VAAPI for decoding and that seems to work good.  I have an HDMI connection from the board to the receiver of course, no adapters or boxes of any kind.  Just straight into the amp.  My tuner is an HDHomerun that works good with OpenELEC on a raspberry pi frontend, and seems to work pretty much the same when playing live TV through MythTV frontend.  


I have ALSA:hdmi:CARD=HDMI,DEV=0 as my audio output device.  I have all the boxes checked for DD, DTS, E-AC-3, TrueHD and DTS-HD since I believe the receiver supports all this.  My speaker configuration is 7.1.  I don't have Upconvert checked and I have the mixer set to external as indicated by several forum posts.


What is really weird is that after restarting the box, I went to the audio test page and sound comes out (PCM Multichannel) of the correct individual speakers, only once though.  Restarting it again and it's wrong again.  When I watch Live TV, things sound okay like it's all mapped the correct way, which would be the natural case since it seems like passthru is happening.  If I exit MythTV frontend and restart it, the audio test (PCM Multichannel) sends sound to the wrong speakers, but LiveTV seems to continue to play ok with the correct mappings every time I try it.  I only saw it work right once, so something odd is going on somewhere.


When testing using the PCM Multichannel, the incorrect mappings are:
```

Should be playing through     Actually plays through
Front Left                     Front Right
Center                         LFE
Front Right                    Rear Left
Surround Left                  Surround Right
LFE                            Surround Left
Surround Right                 Front Left
Rear Left                      Rear Right
Rear Right                     Center

```
I don't find any asound.conf or .asoundrc files anywhere on my system.  Am I doing something stupid, or do I need to create some kind of remapping file?


Output from aplay -l and aplay -L follows.
```
mike@mythbackend:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
hdmi:CARD=HDMI,DEV=0
    HDA Intel HDMI, HDMI 0
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=1
    HDA Intel HDMI, HDMI 1
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=2
    HDA Intel HDMI, HDMI 2
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Direct sample mixing device
dmix:CARD=HDMI,DEV=7
    HDA Intel HDMI, HDMI 1
    Direct sample mixing device
dmix:CARD=HDMI,DEV=8
    HDA Intel HDMI, HDMI 2
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Direct sample snooping device
dsnoop:CARD=HDMI,DEV=7
    HDA Intel HDMI, HDMI 1
    Direct sample snooping device
dsnoop:CARD=HDMI,DEV=8
    HDA Intel HDMI, HDMI 2
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=7
    HDA Intel HDMI, HDMI 1
    Direct hardware device without any conversions
hw:CARD=HDMI,DEV=8
    HDA Intel HDMI, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=7
    HDA Intel HDMI, HDMI 1
    Hardware device with all software conversions
plughw:CARD=HDMI,DEV=8
    HDA Intel HDMI, HDMI 2
    Hardware device with all software conversions
sysdefault:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions
mike@mythbackend:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mike@mythbackend:~$
```


Here's the output of /proc/asound/card0/eld:
```

mike@mythbackend:~$ cat /proc/asound/card0/eld#0.0
monitor_present         1
eld_valid               1
monitor_name            TX-NR828
connection_type         HDMI
eld_version             [0x2] CEA-861D or below
edid_version            [0x3] CEA-861-B, C or D
manufacture_id          0xcb3d
product_id              0xd81
port_id                 0x0
support_hdcp            0
support_ai              1
audio_sync_delay        0
speakers                [0x4f] FL/FR LFE FC RL/RR RLC/RRC
sad_count               8
sad0_coding_type        [0x1] LPCM
sad0_channels           2
sad0_rates              [0x1ee0] 32000 44100 48000 88200 96000 176400 192000
sad0_bits               [0xe0000] 16 20 24
sad1_coding_type        [0x1] LPCM
sad1_channels           8
sad1_rates              [0x1ee0] 32000 44100 48000 88200 96000 176400 192000
sad1_bits               [0xe0000] 16 20 24
sad2_coding_type        [0x2] AC-3
sad2_channels           8
sad2_rates              [0xe0] 32000 44100 48000
sad2_max_bitrate        640000
sad3_coding_type        [0x7] DTS
sad3_channels           8
sad3_rates              [0xc0] 44100 48000
sad3_max_bitrate        1536000
sad4_coding_type        [0x9] DSD (One Bit Audio)
sad4_channels           6
sad4_rates              [0x40] 44100
sad5_coding_type        [0xa] E-AC-3/DD+ (Dolby Digital Plus)
sad5_channels           8
sad5_rates              [0xc0] 44100 48000
sad6_coding_type        [0xb] DTS-HD
sad6_channels           8
sad6_rates              [0x1ec0] 44100 48000 88200 96000 176400 192000
sad7_coding_type        [0xc] MLP (Dolby TrueHD)
sad7_channels           8
sad7_rates              [0x1480] 48000 96000 192000
mike@mythbackend:~$

```

---

