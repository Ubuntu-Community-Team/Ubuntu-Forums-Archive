---
title: "Creative CA0132 no surround sound (only stereo)"
date: 2018-02-04
forum: Hardware
---

### Post by ijml-team on 2018-02-04
Gigabyte Z87 G1.Sniper M5 with Creative CA0132, surround does not work.
Any idea?
ubuntu 16.04 LTS Kernel 4.9.0-040900-generic
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 04)


[https://i.pinimg.com/564x/ae/64/9f/ae649f33532f1dc598e66c6936fe1353.jpg](https://i.pinimg.com/564x/ae/64/9f/ae649f33532f1dc598e66c6936fe1353.jpg)
```

aplay -L
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
    HDA Intel PCH, CA0132 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    Front speakers
surround21:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, CA0132 Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, CA0132 Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, CA0132 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, CA0132 Digital
    Hardware device with all software conversions

```

---

### Post by bcschmerker on 2018-02-05
**This is a known issue for the Creative Laboratories® SoundCore3D® DSP family,** which is only partially supported in ALSA 1.0.25-up under the HDA Intel driver.  HDA Intel can utilize only part of the CA0130 and CA0132 chips, whereas I had complete surround support for the CA0102 (in a Creative Laboratories® SB0350/SB0250 package that failed me September 2017) under ALSA emu10k1.

---

### Post by ijml-team on 2018-02-06
It's difficult to solve this

     The **snd_emu10kx** driver supports the following sound cards:

     **·**   Creative Sound Blaster Live! (EMU10K1 Chipset).  Both PCM and MIDI
         interfaces are available.
     **·**   Creative Sound Blaster Audigy (CA0100 and CA0101 Chipset).  PCM and
         two MIDI interfaces available.
     **·**   Creative Sound Blaster Audigy 2 and Creative Sound Blaster Audigy 4
         (CA0102 Chipset).  PCM support is limited to 48kHz/16 bit stereo
         (192kHz/24 bit part of this chipset is not supported).
     **·**   Creative Sound Blaster Audigy 2 Value (CA0108 Chipset).  PCM support
         is limited to 48kHz/16 bit stereo (192kHz/24 bit part of this chipset
         is not supported).  There is no MIDI support for this card.

do not ca0132

(google english)

---

