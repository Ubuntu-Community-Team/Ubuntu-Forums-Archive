---
title: "No sound with Nvidia MCP51 on HP V3030"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by xenthro on 2007-10-23
Ok. Fresh Gutsy install. No sound. Forums said install alsa 1.0.15 from source and I did (although not sure how good my compiling skills are, and there were about 5 different (but similar?) sets of instructions that I followed), I have reformatted and now have a fresh install with only  linux-backports-modules installed. The results are as such:

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.15rc3.

lsmod

snd_hda_intel         291488  1 
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  2 snd_pcm_oss
snd_pcm                80004  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10244  1 snd_hda_intel
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

and lscpi

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I believe that is all the info. I am running the 32bit gutsy even though my laptop is x_64

Would appreciate some good advice... a bit tired of the 5 versions of a "Shot in the dark"

---

### Post by GregoYatzee on 2007-10-23
I have a HP dv9000 with Realtek Digital Audio and have tried just as you with no success.  I downloaded the tar from Realtek and ran the automatic install.  Install ran through although apparently unsuccessfully.  I tried a couple other instruction sets from other sources and none would even get past first step.  This notebook would not even boot from CD on last version of Ubuntu, Gutsy has everything working but audio.

---

### Post by xenthro on 2007-10-23
I also noticed that using alsamixer only displays the conexant card... I believe it needs to be the alsa card. any way to force this?

---

### Post by msandoy on 2007-10-23
I had a big problem setting up sound on this sound card, but I found the sollution on this page:
[http://jrblevin.freeshell.org/weblog/linux/mcp51-alsa](http://jrblevin.freeshell.org/weblog/linux/mcp51-alsa)

Hope this can be of help to you... :-)

---

