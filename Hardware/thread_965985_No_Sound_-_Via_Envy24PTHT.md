---
title: "No Sound - Via Envy24PT/HT"
date: 2008-11-01
forum: Hardware
---

### Post by ChikyuuKou on 2008-11-01
I just did a clean install of Ubuntu 8.10 and I have no sound. Sound has worked flawlessly on this machine from Edgy to Gutsy thus far.

Here is some info that might be helpful:

```
> uname -a
Linux Linux-Desktop 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux

```

```
> lspci
03:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
```

```
> lsmod
snd_ice1724           101052  0 
snd_ice17xx_ak4xxx     11648  1 snd_ice1724
snd_ac97_codec        111652  1 snd_ice1724
ac97_bus                9856  1 snd_ac97_codec
snd_ak4xxx_adda        16512  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_ak4114             17152  1 snd_ice1724
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  4 snd_ice1724,snd_ac97_codec,snd_ak4114,snd_pcm_oss
snd_page_alloc         16136  1 snd_pcm
snd_pt2258             11904  1 snd_ice1724
snd_i2c                13440  2 snd_ice1724,snd_pt2258
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_ice1724,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  14 snd_ice1724,snd_ac97_codec,snd_ak4xxx_adda,snd_ak4114,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_pt2258,snd_i2c,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
```

```
> lshw
*-multimedia UNCLAIMED
                description: Multimedia audio controller
                product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
                vendor: VIA Technologies Inc.
                physical id: 2
                bus info: pci@0000:03:02.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=32
```

Any help would be appreciated.

---

### Post by ardvark71 on 2008-11-01
Hi...

Does this guide help?

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Best Regards...

---

### Post by ChikyuuKou on 2008-11-01
Unfortunately that guide did not seem to help.

Here is some additional information

```
> dmesg
[   15.242767] ICE1724 0000:03:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.278753] ice1724: No valid ID is found
[   15.278775] ICE1724 0000:03:02.0: PCI INT A disabled
[   15.278798] ICE1724: probe of 0000:03:02.0 failed with error -5
```

```
> lspci -v
03:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
	Flags: medium devsel, IRQ 18
	I/O ports at a400 [size=32]
	I/O ports at a800 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-ice1724
```

```
> aplay -l
aplay: device_list:215: no soundcards found...
```

I put in an 8.04.1 LiveCD and the sound worked fine, but 8.10 doesn't seem to be able to use my soundcard.

---

### Post by ChikyuuKou on 2008-11-01
I installed OSS and now my sound works fine.

---

### Post by ardvark71 on 2008-11-01
> **ChikyuuKou said:**
> I installed OSS and now my sound works fine.

I'm glad! :KS

Best Regards...

---

### Post by clango on 2009-01-10
> **ChikyuuKou said:**
> I installed OSS and now my sound works fine.

Dear friend and friends,

I'm still in trouble where you were. In fact my system doesn't recognize my sound device even if it seem I have, like you the modules snd 1724.

I tried also to install Oss but without any  success. I feel uncomfortable now because I presume I installed too many things. How may I can clean ans start again from zero?

Basically I think the problem is coming because at aplay -l is not recognized the sound card

---

### Post by cabez0n on 2009-11-26
> **ChikyuuKou said:**
> I installed OSS and now my sound works fine.

What was the package you installed to get this working ?
Thanx

---

### Post by clango on 2009-11-30
> **cabez0n said:**
> What was the package you installed to get this working ?
Thanx

Even if I found several friends that tried to helpme, after hours and hours of trials and no solutions, I personally fixed buying a new sound card. Less than 20 Euro. Of course I asked before its compatibility with Linux and now my sound function perfectly!;)

---

