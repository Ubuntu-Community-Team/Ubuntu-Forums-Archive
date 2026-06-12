---
title: "Audio and shutdown on an Olidata Stainer 3050"
date: 2018-07-03
forum: Hardware
---

### Post by 4l3x2 on 2018-07-03
Good afternoon,

I installed Lubuntu 18.04 64bit on the laptop of a colleague of mine, in dual boot with Win 7 32bit.

I have 2 issues:
- if I try to shutdown or to reboot Linux it hangs on the Lubuntu screen, only the first 2 dots change their color but after it I have to push the shutdown button to effectively turn off the pc
- the audio doesn't work properly: in the pavucontrol I can only see the dummy output, but if I try to ask for the hardware/modules installed I can see the snd peripherals.
I'll show the output of some commands:

lspci | grep Audio:

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)

lsmod | grep snd:

snd_hda_codec_realtek    94208  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_codec_si3054    16384  1
snd_hda_intel          40960  5
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_si3054,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_si3054,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  5 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_si3054
snd_timer              32768  1 snd_pcm
snd                    81920  17 snd_hda_intel,snd_hwdep,snd_hda_codec,snd_timer,snd_hda_codec_generic,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd

dmesg | grep snd:

[   29.327235] snd_hda_codec_realtek hdaudioC0D1: ALC883: SKU not ready 0x598301f0
[   29.327563] snd_hda_codec_realtek hdaudioC0D1: autoconfig for ALC883: line_outs=1 (0x15/0x0/0x0/0x0/0x0) type:speaker
[   29.327567] snd_hda_codec_realtek hdaudioC0D1:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   29.327578] snd_hda_codec_realtek hdaudioC0D1:    hp_outs=1 (0x14/0x0/0x0/0x0/0x0)
[   29.327580] snd_hda_codec_realtek hdaudioC0D1:    mono: mono_out=0x0
[   29.327583] snd_hda_codec_realtek hdaudioC0D1:    dig-out=0x1e/0x0
[   29.327585] snd_hda_codec_realtek hdaudioC0D1:    inputs:
[   29.327588] snd_hda_codec_realtek hdaudioC0D1:      Internal Mic=0x19
[   29.327591] snd_hda_codec_realtek hdaudioC0D1:      Mic=0x18


Can you help me to solve this issue?
If I try to lauch Win 7 the audio is correctly played and in the bios I couldn't find any option to enable/disable/configure audio.

Thank you in advance

---

