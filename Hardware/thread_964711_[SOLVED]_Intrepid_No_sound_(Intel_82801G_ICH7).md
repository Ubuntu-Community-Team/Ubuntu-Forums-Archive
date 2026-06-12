---
title: "[SOLVED] Intrepid: No sound (Intel 82801G ICH7)"
date: 2008-10-31
forum: Hardware
---

### Post by djvishnu on 2008-10-31
Hi, just installed 8.10 (fresh), and I got _no sound_ :(

I remember this happened with hardy as well, but cant remember what i did to fix it.

I really need help, my work day get's alot harder without last.fm. Here are some clues:

```
> lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

```
> lsmod | grep intel
snd_hda_intel         381488  0 
snd_pcm                83204  1 snd_hda_intel
snd                    63268  3 snd_hda_intel,snd_pcm,snd_timer
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
intel_agp              33724  0 
agpgart                42184  2 nvidia,intel_agp
```

```
> lshw (..)
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```


Any ideas? I couldn't find any recent bug reports.

If i try to play something with, e.g., _mplayer_, i get:
```
> mplayer somehting.mp3
AO: [pulse] Failed to connect to server: Connection refused
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
.....
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
...
...
AO: [null] 44100Hz 2ch s16le (2 bytes per sample)
...playing silently.

```



**EDIT:**
```
> cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xde400000 irq 21

```

---

### Post by djvishnu on 2008-10-31
Well. this was a waste of time. Entirely my fault.

"sudo apt-get install linux-sound-base" did the trick. :shock:

I'll never make that mistake again..

---

### Post by coolacid217 on 2008-11-01
I have the same problem, and when I try to install the linux-sound-base package, it says to me that the most recent version is already installed. What can I do?

---

### Post by djvishnu on 2008-11-02
What does "aplay -l" and "lsmod | grep intel" say?

The reason i had to install linux-sound-base was that i had used the "command line system" option when installing, creating a minimal install - without sound. A standard ubuntu-desktop install *should* include everything needed for sound.

---

### Post by realmagnum on 2008-12-31
I used command line installation too, and I have the same problem: I have no sound.

But install linux-sound-base package didn't solve my problem. Like coolacid217, this package was already installed.

When I do a complete installation, sound is ok. So, I only have to find the missing package.

Some information:

lspci | grep Audio

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


lsmod | grep intel

snd_hda_intel         381488  3 
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  0 
agpgart                42184  1 intel_agp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm


lshw

WARNING: you should run this program as super-user.
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel


cat /proc/asound/cards

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 21


aplay -l

**** Lista de Dispositivos PLAYBACK Hardware ****
placa 0: Intel [HDA Intel], dispositivo 0: AD198x Analog [AD198x Analog]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 0: Intel [HDA Intel], dispositivo 1: AD198x Digital [AD198x Digital]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 0: Intel [HDA Intel], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0

---

