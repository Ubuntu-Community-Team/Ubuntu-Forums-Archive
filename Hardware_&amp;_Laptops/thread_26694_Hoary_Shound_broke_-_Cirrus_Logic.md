---
title: "Hoary Shound broke - Cirrus Logic"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by mish on 2005-04-13
Like many others, my sound broke when I upgraded from Warty to Hoary.  If I boot up using the Warty kernel (2.6.8) then the sound works fine.  But it would be nice to get it working with the new kernel ...

With the new kernel I never get errors.  Everything seems to work fine, the volume monitor shows signel levels, but no sound comes out of the speakers.  I have a Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator]

I've searched throught the forums and tried various things with no success as yet.

alsamixer - IEC958 xxx are all muted.  Other ones appear to be at reasonable levels.

I've tried a couple of different edits of esd.conf - no luck there

Output of lsmod | grep snd

```

snd_cs46xx             86664  2
snd_rawmidi            24928  1 snd_cs46xx
snd_seq_device          8524  1 snd_rawmidi
snd_ac97_codec         74208  1 snd_cs46xx
snd_pcm_oss            52516  1
snd_mixer_oss          19776  2 snd_pcm_oss
snd_pcm                94920  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25156  1 snd_pcm
snd                    55268  8 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10080  3 snd
snd_page_alloc          9796  2 snd_cs46xx,snd_pcm
gameport                4544  2 snd_cs46xx,analog

```

Output of lspci

```

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:07.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:08.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]

```

Output of lsof 

```

~ $ lsof /dev/dsp
COMMAND  PID   USER   FD   TYPE DEVICE SIZE NODE NAME
esd     7795 hamish    5w   CHR   14,3      6821 /dev/dsp
~ $
~ $ lsof /dev/snd/*
~ $

```

Though if I killall esd first then lsof /dev/dsp returns nothing.

Does anyone know if the fix for Audigy 2 sound cards from thread [http://www.ubuntuforums.org/showthread.php?t=21211](http://www.ubuntuforums.org/showthread.php?t=21211) will work for other sound cards.  That's the one thing I've yet to try - it looks like rolling back might be a bit harder.

Any bright ideas out there?

---

