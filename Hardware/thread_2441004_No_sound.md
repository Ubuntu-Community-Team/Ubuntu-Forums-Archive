---
title: "No sound"
date: 2020-04-17
forum: Hardware
---

### Post by kklive on 2020-04-17
Hello,
on a relatively old ASUS laptop, I initially replaced the original Windows Vista with Linux Mint 19.3 XFCE. However, since this was very tough, I have now switched to Xubuntu 18.04.4 LTS.

As with Linux Mint, there is no sound with Xubuntu. The loudspeaker is "not available" in pavucontrol. After the new installation I added the line in "alsa-base.conf":
```
options snd-hda-intel model = generic
```
The sound output worked after a restart. After another restart, no sound comes out. All combinations with options snd-hda-intel model = xxxxx probe_mask = xxx also do not work.

The same thing happens (again after a new installation) after one
```
sudo alsactl init
alsactl store
```
At first everything works after a restart, but nothing works after another restart.

Here is some system information:
```
dmesg
[    0.321129] ACPI: Added _OSI(Linux-Dell-Video)
[    0.321132] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.321134] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
--
[   18.134110] ath5k 0000:04:00.0: registered as 'phy0'
[   18.389494] snd_hda_codec_generic hdaudioC0D0: autoconfig for Generic: line_outs=1 (0x1b/0x0/0x0/0x0/0x0) type:speaker
[   18.389500] snd_hda_codec_generic hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.389503] snd_hda_codec_generic hdaudioC0D0:    hp_outs=1 (0x1a/0x0/0x0/0x0/0x0)
[   18.389505] snd_hda_codec_generic hdaudioC0D0:    mono: mono_out=0x0
[   18.389507] snd_hda_codec_generic hdaudioC0D0:    inputs:
[   18.389510] snd_hda_codec_generic hdaudioC0D0:      Mic=0x1f
[   18.406286] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   18.406423] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   18.459559] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
-e
```
The speaker channel is of course not muted in the alsamixer!

I recently posted this problem to the german Ubuntu-Forums, but it could not be solved. I hope, someone can help me here!

---

