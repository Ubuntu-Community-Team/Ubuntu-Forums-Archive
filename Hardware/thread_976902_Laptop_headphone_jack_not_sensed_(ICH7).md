---
title: "Laptop headphone jack not sensed (ICH7)"
date: 2008-11-09
forum: Hardware
---

### Post by NightMKoder on 2008-11-09
There's been tons of threads on this, but I couldn't find a solution in any one of them. I know there is supposed to be a switch for enabling headphone sensing, but its not in KMix at all nor is it in alsamixer. So here goes:

Fujitsu T4215
Kubuntu Intrepid
Kernel: 2.6.27-7-generic
ALSA: 1.0.17
Kernel Module: snd-hda-intel

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

```

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
$ lspci -vv -s 00:1b.0
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Fujitsu Limited. Device 13b4
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at f0640000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

```

$ lsmod | grep snd
snd_hda_intel         428436  5
snd_pcm_oss            46496  0
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                83844  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         16776  2 snd_hda_intel,snd_pcm
snd_hwdep              15492  1 snd_hda_intel
snd_seq_dummy          11012  0
snd_seq_oss            39936  0
snd_seq_midi           14368  0
snd_rawmidi            29728  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                58480  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29448  3 snd_pcm,snd_seq
snd_seq_device         15500  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    66212  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd

```

```

$ head -n 1 /proc/asound/*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9228

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/Intel/codec#0 <==
Codec: SigmaTel STAC9228

==> /proc/asound/Intel/codec#1 <==
Codec: LSI ID 1040

```

I've tried all the options for STAC9228 from [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt), all of which simply killed my sound altogether. I also tried 'fujitsu', which also didn't give any results.

My current setup:
```

$ tail -n 2 /etc/modprobe.d/alsa-base
options snd-hda-intel model=auto position_fix=2

```

Although technically, everything works without it. I also saw some messages on dmesg at boot that I wasn't sure were normal or not

```

$ dmesg | grep HDA
[   12.689800] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   12.689817] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.689846] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.080191] input: HDA Intel at 0xf0640000 irq 17 Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input13
[   14.081222] input: HDA Intel at 0xf0640000 irq 17 HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input14

```

This didn't happen in hardy, but once I switched to intrepid (not upgraded, reinstalled) it no longer works. I tested again with the livecd and it does not work there either. I also tried installing alsa 1.0.18, which did not change anything.

Is this fixable?

---

### Post by haritia on 2009-03-18
was this ever resolved for you?

---

### Post by JDHarper on 2010-05-11
I'm having this same issue; Fujitsu T4215, no headphone jack sense on a fresh install of Kubuntu Lucid Lynx. 

alsamixergui tells me that it has the following:
Board: HDA Intel
Chip: SigmaTel STAC9228

Any ideas?

---

### Post by lidex on 2010-05-13
Start here. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

---

