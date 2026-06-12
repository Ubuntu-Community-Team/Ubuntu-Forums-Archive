---
title: "Sound Cracking / Stuttering When Using ALSA"
date: 2016-04-08
forum: Hardware
---

### Post by SolarLune on 2016-04-08
Hey. 

So my problem is that basically, the sound crackles when programs use ALSA for their sound driver (?). If the programs use SDL, or something else (Chromium doesn't seem to use ALSA for sound output), then everything sounds file. However, if the program uses ALSA, then most of the time, the audio is really crackly and stuttery. Sometimes it resolves itself, other times it doesn't. Sometimes it goes from crackly, to clear, and then back to crackly. When the sound's crackly, the stream doesn't show up in pavucontrol, so maybe it's something to do with driver not being able to start the stream or something?

Also, when I examine the System Monitor, I can see pulseaudio and pavucontrol taking up way more CPU than normal when this happens (from 0% to 17%), and I can see all 6 of my CPU cores working way harder than they should (from around 7% with a program using SDL to around 35% with it using ALSA). Again, this happens with multiple programs, so it's definitely ALSA itself at the root of this. I've tried different workarounds like setting tsched=0 in the etc/pulse/default.pa, and reinstalling PulseAudio, but none of them worked, at least, not so far.

lspci -v | grep Audio output:

```

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
01:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1)

```

aplay -l output:

```
card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Microphone [Yeti Stereo Microphone], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

For hardware, I'm running a MSI 970A-G43 Plus motherboard, an AMD-FX6350 Six-core processor, an NVIDIA Geforce GTX 660 graphics card, 8 GB of Kingston HyperX RAM, and Ubuntu Gnome 15.10.

Any ideas?

EDIT: Uninstalling and reinstalling alsa-utils didn't work.

For reference, the program I am using to quickly test this out is Sunvox. In Sunvox, you can specify which driver, frequency, and latency to use for audio playback, and when it's on Alsa, it usually starts off with crackling audio, and plays back the audio exceptionally quickly. If Sunvox is open for awhile it eventually fixes itself.

---

### Post by SolarLune on 2016-04-11
Hey, so I've got an update. It seems like this only becomes a problem if I have my Blue Yeti USB microphone plugged in. I get pretty much perfect audio (slight stuttering at the beginning when playing a game through Wine), but once I plug the USB cord in - instant stuttersville.

Any tips?

---

### Post by SolarLune on 2016-05-02
So it seems the latest version of Ubuntu (16.04) might have solved the issue. Hurrah!

---

