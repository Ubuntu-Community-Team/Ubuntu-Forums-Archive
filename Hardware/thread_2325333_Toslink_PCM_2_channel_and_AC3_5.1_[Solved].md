---
title: "Toslink PCM 2 channel and AC3 5.1 [Solved]"
date: 2016-05-21
forum: Hardware
---

### Post by BatteryKing on 2016-05-21
While getting full Toslink support to work in a satisfactory manner under Ubuntu 14.04 LTS, I came across some caveats that I did not see well documented, so I thought I should post my experiences on the subject.

The first device I tried to get working is a SoundBaster Live! 24-bit USB device, model SB0490.  At first what I came across was it would play 2 channel PCM over Toslink when I set it in analogue stereo mode.  If I set it to "Digital Stereo (IEC958) Output", no sound came out, which I will describe the solution to below.  I followed these ([https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)) instructions to setup surround sound via AC3.  While I got new options in Pulseaudio, it was highly unstable and the sound system kept crashing.  I did find a solution to this, which I will talk about next.

I ended up picking up an Asus Xonar DGX PCIe card at a local Fry's.  This card is basically their PCI card except with a PCIe 1x to PCI 32-bit bridge chip.  Just plugging the Toslink cable into this card and using it instead of the the SoundBlaster USB device caused AC3 to work reliably.  I did notice one thing in that while 448 kbit/s AC3 sounds alright, there was a rather noticeable degradation in sound quality, especially at the higher frequencies and for more complex sounds, even bass sounded a bit distorted, and in general just sounded softer.  I played with bitrates some and found at least for the Sony STR-K7000 I recently got my hands on (I received it as a hand me down for free, so couldn't complain about price) that I could set the bitrate at 896 kbit/s and it seemed to work.  It seemed to sound a little better, but there was still a significant amount of loss in quality.  At this point 2 channel PCM was not working at all; I just saw the options but no sound, so I investigated further and found an answer documented below.  I also got 6 channel (5.1 surround) sound to work with mplayer using the "-channels 6" option, but I never did get AC3 passthrough to work.  Anyways movie tracks tend to be so quite it is nice to be able to increase the volume level in software with mplayer so you don't get completely blasted out when you switch back to other audio sources and it is nice to be able to multitask audio which I don't think you normally get if you do AC3 passthrough.

Getting back to making 2 channel PCM work, the interesting thing was the Pulseaudio mixer showed everything as there and not muted, but no sound even though AC3 worked over the same interface.  Digging through config files, I found in the file /usr/share/pulseaudio/alsa-mixer/paths/iec958-stereo-output.conf that the mute option was set.  Commenting this line out and reloading alsa and restarting pulseaudio seemed to fix the problem.  Finally some sort of degradation free audio for what 2 channels at 16 bits and 48 KHz is worth.  (The most common use of this sound system is to play music while I work on my pet projects and make posts like this for which the aforementioned quality level is fine for and really no worse than the 16-bit 44.1 KHz source I have access to while leaving things open for the occasional surround sound action.)

---

