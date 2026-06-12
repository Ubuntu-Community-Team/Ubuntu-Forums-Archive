---
title: "T61 Hardy audio volume works but very low"
date: 2008-08-29
forum: Hardware
---

### Post by salamander71 on 2008-08-29
My T61 Thinkpad runs 8.04 Ubuntu, and most everything seems to have worked at install.  However, though the audio volume is audible, it's very low.  While this is not a critical issue for me, it'd be nice if I could raise it.

Here is what I believe to be relevant information.
- Alsamixer shows 100% on Master and PCM, both are at 00
-  lsmod|grep hda
snd_hda_intel         440408  3 
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

so I have my module OK, it seems

- the sound applet up by the clock shows master and pcm set to 100% under playback, and under switches, both headphone and speaker are checked.  Continuing to preferences on that same applet, master is highlighted under HDA Intel (Alsa Mixer) (note: some posters have said to highlight both master and pcm under the "device to control" menu, but I have not succeeded in doing this)

- as to the system > preferences > sound, "default mixer tracks" is set to HDA Intel (Alsa Mixer) and Master is highlighted

- the T61 buttons to the left of the "ThinkVantage" blue button are appropriately set (at maximum)

Anyone have any ideas how I can get more volume out of my laptop?

Thanks in advance

---

### Post by benplus on 2008-09-16
install alsa-utils 
run alsamixer
check the volume of each item

---

