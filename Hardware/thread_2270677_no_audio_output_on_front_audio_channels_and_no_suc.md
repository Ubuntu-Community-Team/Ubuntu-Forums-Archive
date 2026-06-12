---
title: "no audio output on front audio channels and no success mapping with asound.conf"
date: 2015-03-24
forum: Hardware
---

### Post by fritz7 on 2015-03-24
Hello guys,

I have the problem that there is no sound output on the 2 front channels with linux (mint 17). The 2 rear channels and die subwoofer channels are working. I have not tested the centre channel. I use the 3.16.0-31-generic kernel and with windows everything is working fine so I have not connected anything wrong.

I tried to remap the channels with /etc/asound.conf which is used by the system because if I make syntax errors speaker-test complains about it. However I see/hear no difference if i test it with "speaker-test -c 6 -r 48000". When I use "speaker-test -c 6 -r 48000 -D pcm.duplex" I get the following error
**speaker-test -c 6 -r 48000 -D pcm.duplex**
```

speaker-test 1.0.27.2

Wiedergabe-Gerät ist pcm.duplex
Stream-Parameter sind 48000 Hz, S16_LE, 6 Kanäle
Verwende 16 Oktaven rosa Rauschen
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
Fehler beim Öffnen des Gerätes: -16, Das Gerät oder die Ressource ist belegt <= this means error while opening device, ressource is allready in use

```

while playing around I also recognized a strange behaviour. In pavucontrol it is possible to control the volume of each channel on it's own ... usually ... in my case the highest level is the level for all channels and the other values were ignored.

At the end of the post I added some information I hope this is usefull to help me with my problem. If something is missing pleas tell me and I'll ad it. Maybe someone can give me a hint to solve the problem and thanks for reading

**/etc/asound.conf**
```

#/etc/asound.conf

pcm.!default {
        type hw
        card 0
        device 0
}

pcm.snd_card {
        type hw
        card 0
        device 0
}

ctl.snd_card {
        type hw
        card 0
        device 0
}

pcm.swap51 {
    type dmix
    ipc_key 1024
    ipc_perm 0666
    slave.pcm "snd_card"
    slave {
        channels 6 
    }
    bindings {
     0 2
     1 3
     2 0
     3 1
     4 4
     5 5
   }
}

pcm.duplex {
    type asym
    playback.pcm "swap51"
}

pcm.!default {
    type plug
    slave.pcm "duplex"
}

```
[B]
 aplay -L[/B]
```
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
swap51
duplex
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC1150 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC1150 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC1150 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC1150 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC1150 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC1150 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC1150 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC1150 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC1150 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC1150 Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC1150 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC1150 Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC1150 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC1150 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC1150 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC1150 Digital
    Hardware device with all software conversions
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
hdmi:CARD=Generic,DEV=1
    HD-Audio Generic, HDMI 1
    HDMI Audio Output
hdmi:CARD=Generic,DEV=2
    HD-Audio Generic, HDMI 2
    HDMI Audio Output
hdmi:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 3
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dmix:CARD=Generic,DEV=7
    HD-Audio Generic, HDMI 1
    Direct sample mixing device
dmix:CARD=Generic,DEV=8
    HD-Audio Generic, HDMI 2
    Direct sample mixing device
dmix:CARD=Generic,DEV=9
    HD-Audio Generic, HDMI 3
    Direct sample mixing device
dmix:CARD=Generic,DEV=10
    HD-Audio Generic, HDMI 4
    Direct sample mixing device
dmix:CARD=Generic,DEV=11
    HD-Audio Generic, HDMI 5
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
dsnoop:CARD=Generic,DEV=7
    HD-Audio Generic, HDMI 1
    Direct sample snooping device
dsnoop:CARD=Generic,DEV=8
    HD-Audio Generic, HDMI 2
    Direct sample snooping device
dsnoop:CARD=Generic,DEV=9
    HD-Audio Generic, HDMI 3
    Direct sample snooping device
dsnoop:CARD=Generic,DEV=10
    HD-Audio Generic, HDMI 4
    Direct sample snooping device
dsnoop:CARD=Generic,DEV=11
    HD-Audio Generic, HDMI 5
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
hw:CARD=Generic,DEV=7
    HD-Audio Generic, HDMI 1
    Direct hardware device without any conversions
hw:CARD=Generic,DEV=8
    HD-Audio Generic, HDMI 2
    Direct hardware device without any conversions
hw:CARD=Generic,DEV=9
    HD-Audio Generic, HDMI 3
    Direct hardware device without any conversions
hw:CARD=Generic,DEV=10
    HD-Audio Generic, HDMI 4
    Direct hardware device without any conversions
hw:CARD=Generic,DEV=11
    HD-Audio Generic, HDMI 5
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions
plughw:CARD=Generic,DEV=7
    HD-Audio Generic, HDMI 1
    Hardware device with all software conversions
plughw:CARD=Generic,DEV=8
    HD-Audio Generic, HDMI 2
    Hardware device with all software conversions
plughw:CARD=Generic,DEV=9
    HD-Audio Generic, HDMI 3
    Hardware device with all software conversions
plughw:CARD=Generic,DEV=10
    HD-Audio Generic, HDMI 4
    Hardware device with all software conversions
plughw:CARD=Generic,DEV=11
    HD-Audio Generic, HDMI 5
    Hardware device with all software conversions
```

[B]
lspci -nnk | grep -iA2 audio[/B]
```
00:1b.0 Audio device [0403]: Intel Corporation Device [8086:8ca0]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:a182]
    Kernel driver in use: snd_hda_intel
--
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:aac8]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:aac8]
    Kernel driver in use: snd_hda_intel
```

---

### Post by Yellow Pasque on 2015-03-24
Pulseaudio is meant to replace dmix, so I'd try removing the asound.conf entirely. Technically, you can set both of them up to play nicely together, but I don't think that's your goal.  (Note that in your example, trying to play to pcm.duplex doesn't work because pulseaudio has already grabbed the sound device).

Look at /etc/pulse/daemon.conf and make sure default-sample-channels=6. You can also change the mapping if the channels are mapped to wrong speakers, and maybe you want to change enable-lfe-remixing to 'yes'.
REMINDER: You have to uncomment a line by removing the leading '#' if you want it to be read.

---

