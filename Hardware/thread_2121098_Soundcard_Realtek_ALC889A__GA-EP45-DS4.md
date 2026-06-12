---
title: "Soundcard Realtek ALC889A | GA-EP45-DS4"
date: 2013-02-28
forum: Hardware
---

### Post by szaman86 on 2013-02-28
[FONT=Arial][COLOR=#006ffd][B]Hi!

[/B][/COLOR][/FONT][COLOR=#0000cd][FONT=Arial][SIZE=3]I have a problem with running sound-card Realtek ALC889A on my Ubuntu 12.10 machine.
I already visited plenty of forums with treated about sound-cards problem on Debian. 

I downloaded drivers and utilities from Realtek website, which are: 

[/SIZE][/FONT][/COLOR][COLOR=#808080][SIZE=2]realtek-linux-audiopack-5.17[/SIZE][/COLOR][COLOR=#000000][SIZE=2] included[/SIZE][/COLOR][COLOR=#808080]alsa-driver-1.0.25[SIZE=2]

[/SIZE][/COLOR][COLOR=#0000CD][FONT=Arial]Here is [/FONT][/COLOR][COLOR=#2f4f4f]modprobe [/COLOR][COLOR=#0000CD][FONT=Arial]results

[/FONT][/COLOR]kernel/sound/soundcore.ko
kernel/sound/pci/hda/snd-hda-codec.ko
kernel/sound/pci/hda/snd-hda-codec-realtek.ko
kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
kernel/sound/pci/hda/snd-hda-codec-analog.ko
kernel/sound/pci/hda/snd-hda-codec-idt.ko
kernel/sound/pci/hda/snd-hda-codec-si3054.ko
kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
kernel/sound/pci/hda/snd-hda-codec-conexant.ko
kernel/sound/pci/hda/snd-hda-codec-via.ko
kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
kernel/sound/pci/hda/snd-hda-intel.ko
kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
kernel/sound/acore/snd-pcm.ko
kernel/sound/acore/snd-hwdep.ko
kernel/sound/acore/snd-page-alloc.ko
kernel/sound/acore/oss/snd-pcm-oss.ko
kernel/sound/acore/oss/snd-mixer-oss.ko
kernel/sound/acore/snd-timer.ko
kernel/sound/acore/seq/snd-seq-midi-event.ko
kernel/sound/acore/seq/snd-seq.ko
kernel/sound/acore/seq/oss/snd-seq-oss.ko
kernel/sound/acore/seq/snd-seq-device.ko
kernel/sound/acore/snd.ko

[COLOR=#0000CD][FONT=Arial]Here is [/FONT][/COLOR]cat /proc/asound/cards [COLOR=#0000CD][FONT=Arial]results

[/FONT][/COLOR]--- no soundcards ---


[FONT=Arial][SIZE=3][COLOR=#0000cd]I'm little confused right now so I'm not sure what else I may show you for fionding a solution. I will try to correct this post when my mind will refresh.

Looking forward to see your new ideas[/COLOR][/SIZE][/FONT]

---

