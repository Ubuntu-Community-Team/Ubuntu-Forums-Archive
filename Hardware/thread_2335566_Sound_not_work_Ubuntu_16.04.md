---
title: "Sound not work Ubuntu 16.04"
date: 2016-08-30
forum: Hardware
---

### Post by lolipop2005 on 2016-08-30
Hello, sorry for my english. No work sound on speaker, only headphone. Re-install Ubuntu and also still i have the same problem. Check the following:

dmseg
```
[   11.926577] snd_hda_codec_conexant hdaudioC0D0: CX20585: BIOS auto-probing.
[   11.927207] snd_hda_codec_conexant hdaudioC0D0: autoconfig for CX20585: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[   11.927210] snd_hda_codec_conexant hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   11.927213] snd_hda_codec_conexant hdaudioC0D0:    hp_outs=1 (0x19/0x0/0x0/0x0/0x0)
[   11.927214] snd_hda_codec_conexant hdaudioC0D0:    mono: mono_out=0x0
[   11.927216] snd_hda_codec_conexant hdaudioC0D0:    inputs:
[   11.927218] snd_hda_codec_conexant hdaudioC0D0:      Internal Mic=0x23
[   11.927220] snd_hda_codec_conexant hdaudioC0D0:      Mic=0x1a
[   11.928286] snd_hda_codec_conexant hdaudioC0D0: Enable sync_write for stable communication
```
alsamixer is the volume full, not mutted

My sound card is 

```
Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Toshiba America Info Systems 6 Series/C200 Series Chipset Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at c0600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
```

```
[FONT=UbuntuMono]rm -r ~/.config/pulse/* ; rm -r ~/.pulse[/FONT]
```

```
[FONT=UbuntuMono]options snd-hda-intel model=auto[/FONT]
```

The codec is:

```
cat /proc/asound/car*/co* |  grep Codec
Codec: Conexant CX20585
Codec: Intel CougarPoint HDMI
```

With aplay neither works sound on speaker. 

The only way to recover the sound is rebooting or write in the terminal:

```
sudo pulseaudio -k
sudo alsa force-reload
```

Kernel

```
Linux loli-pc 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

Reset the BIOS to factory default too.

The notebook is Toshiba L745-SP4210.

Thanks you for reading.

Loli

---

### Post by howefield on 2016-08-30
Thread moved to the "*Hardware*" forum for a better fit.

---

### Post by lolipop2005 on 2016-08-30
Any idea?

---

