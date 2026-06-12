---
title: "Toshiba Tecra M3 - No Sound - Need ALSA Help"
date: 2009-03-04
forum: Hardware
---

### Post by vgrisham on 2009-03-04
I've been given a Toshiba Tecra M3 to use at my school. I've got Ubuntu 8.10 Intrepid installed (32-bit), and I can't get it to make any sounds. I know the sound card works because I've got it setup as dual-boot with XP.

I've checked all of the volume levels and they're maxed. 

I googled my problem and found that I need to ["Use the snd-intel8x0 module"]("http://www.linlap.com/wiki/toshiba+tecra+m3") in ALSA. I don't have a clue how to do that. I went to the [ALSA site]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0m") and I don't understand what I'm looking at there.

Can anyone out there help me?

EDIT: I tried reinstalling ALSA as per the Comprehensive Sound Problem thread.

---

### Post by vgrisham on 2009-03-04
Here's my sound related output from lspci -v:

> 
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device 0247
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ae00 [size=256]
    I/O ports at adc0 [size=64]
    Memory at cdaffe00 (32-bit, non-prefetchable) [size=512]
    Memory at cdaffd00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0


---

### Post by vgrisham on 2009-03-04
EDIT: Sound works when I boot to the live cd.

EDIT: Adding output from...
> 
vgrisham@ubuntu:~$ lsmod | grep snd
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm



---

### Post by vgrisham on 2009-03-04
FIXED!!!

Man, the next laptop I buy is going to be a System76. [Here's the solution]("http://ubuntuforums.org/showthread.php?t=1012179") (yes, even for a Toshiba Tecra).

Short answer, double click on your volume icon, and then enable External Amplifier on the Switches tab.

---

