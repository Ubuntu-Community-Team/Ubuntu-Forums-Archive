---
title: "SB live not hardware mixing with alsa/oss emulation?"
date: 2004-11-08
forum: Hardware &amp; Laptops
---

### Post by Redemption042 on 2004-11-08
I've installed ubuntu successfully.  Everything on my system is detected correctly.  one problem I discovered, though, as went to play my favorite game was that /dev/dsp would act as if it only had one channel for OSS devices.  I would start up TeamSpeak, an OSS program that grabs /dev/dsp, and the try te start up Enemy Territory.   Enemy Territory would then freeze on sound init because it too would try to grab /dev/dsp.  The odd thing about this is that my soundcard, the emu10k1 chipset based SB live supports hardware mixing.  In fact, when I had OSS only on my old knoppix based install, teamspeak would work fine with et.   Do I have something not configured right with alsa?

here is the list of modules running in terms of sound.
snd_emu10k1            98184  3
snd_rawmidi            25024  1 snd_emu10k1
snd_pcm_oss            53672  0
snd_mixer_oss          21632  3 snd_pcm_oss
snd_pcm                92704  2 snd_emu10k1,snd_pcm_oss
snd_timer              26628  1 snd_pcm
snd_seq_device         10760  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         71172  1 snd_emu10k1
snd_page_alloc         13192  2 snd_emu10k1,snd_pcm
snd_util_mem            7424  1 snd_emu10k1
snd_hwdep              11552  1 snd_emu10k1
snd                    51940  12 snd_emu10k1,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_seq_device,snd_ac97_codec,snd_util_mem,snd_hwdep
soundcore              11872  3 snd

Here is info from my /proc/asound:
/proc/asound/pcm:
00-00: emu10k1 : EMU10K1 : playback 32 : capture 1
00-01: emu10k1 mic : EMU10K1 MIC : capture 1
00-02: emu10k1 efx : EMU10K1 EFX : capture 1
00-03: emu10k1 : EMU10K1 FX8010 : playback 8

/proc/asound/devices:
  0: [0- 0]: ctl
  4: [0- 0]: hardware dependent
  8: [0- 0]: raw midi
 19: [0- 3]: digital audio playback
 26: [0- 2]: digital audio capture
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
 33:       : timer

Please, PLEASE, someone help me. I've been banging my head at this for two days now and I still don't even know what the problem is.

 :confused:

---

