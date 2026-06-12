---
title: "ALSA Problems"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by alaithea on 2005-06-27
Hi, I've searched and tried everything I can come up with, and I still can't get ALSA to work. I have sound working fine with ESD, but I'm a musician, and want to be able to use all those cool recording/sequencing apps out there for ALSA. (Right now, if I try to start Rosegarden, it just throws errors at me, and then locks up.)

I've got a SoundBlaster Live! 24-bit, but I couldn't get that to work at all, so I pulled it out and switched back to my on-board nVidia NForce2 (intel8x0) sound. So as I said, ESD works fine. But if I go into the Multimedia Systems Selector and test ALSA and OSS, they both will throw the error "Failed to construct test pipeline."

In another thread, I saw the suggestion to install libesd-alsa0. When I did this, Synaptic uninstalled libesd0. So after that ESD gave me the pipeline error, as did ALSA (just as before), and only OSS worked  ](*,) 

Here are the results from my aadebug. It's curious to me that Synaptic says I've got the 1.0.8-4 package, yet aadebug says I've got 1.0.6

> ALSA Audio Debug v0.0.9 - Mon Jun 27 12:41:31 EDT 2005
[http://alsa.opensrc.org/?page=aadebug](http://alsa.opensrc.org/?page=aadebug)

Kernel ----------------------------------------------------
Linux shuttle 2.6.10-5-k7 #1 Fri Jun 24 18:51:20 UTC 2005 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           32416  1
snd_ac97_codec         74208  1 snd_intel8x0
snd_pcm_oss            52516  0
snd_mixer_oss          19776  2 snd_pcm_oss
snd_pcm                94920  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25156  1 snd_pcm
snd                    55268  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc          9796  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
alias char-major-116 snd
alias snd-card-0 snd-intel8x0
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.6 (Sun Aug 15 07:17:53 2004 UTC).
Compiled on Jun 24 2005 for kernel 2.6.10-5-k7.
0 [nForce2        ]: NFORCE - NVidia nForce2
                     NVidia nForce2 with ALC650E at 0xee082000, irq 21
  0: [0- 0]: ctl
 18: [0- 2]: digital audio playback
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
 33:       : timer
cat: /proc/asound/hwdep: No such file or directory
00-00: Intel ICH : NVidia nForce2 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : NVidia nForce2 - MIC ADC : capture 1
00-02: Intel ICH - IEC958 : NVidia nForce2 - IEC958 : playback 1

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D2p  timer

CPU -------------------------------------------------------
model name      : AMD Athlon(tm)
cpu MHz         : 1597.778

RAM -------------------------------------------------------
MemTotal:       484224 kB
SwapTotal:     1413680 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)


Any ideas? Thanks.

P.S. If I try to manually configure and install the latest downloaded ALSA driver according to the docs on the alsa site, it gives me the error that intel8x0 is an unsupported soundcard. Also, if I try to run alsamixer at the command line, I get the following error: "alsamixer: function snd_ctl_open failed for default: No such file or directory"

---

### Post by intangible on 2005-06-27
Here ya go, just realized there wasn't a good enough howto for you, so I made one:
[http://www.ubuntuforums.org/showthread.php?p=230948](http://www.ubuntuforums.org/showthread.php?p=230948)

---

### Post by alaithea on 2005-06-29
Thanks so much! After weeks of trying, your HOWTO has given me sound through ALSA! 

(Now I just need to figure out the ins and outs of midi sequencer setups and using Jack... heh heh.)

---

