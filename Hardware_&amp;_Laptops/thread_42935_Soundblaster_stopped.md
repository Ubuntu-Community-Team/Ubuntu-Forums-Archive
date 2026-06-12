---
title: "Soundblaster stopped"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by DaMasta on 2005-06-20
So my soundblaster (emu10k1) stopped for some reason. Works in windows, not in Hoary. I ran lsmod | grep oss and this is what it returns:
[B]
snd_pcm_oss            47652  1
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd                    50276  9 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep[/B]

I modprobed emu10k1 with no errors. Beep shows a song playing but no sound. Any ideas?

---

### Post by intangible on 2005-06-20
Looks like all the right modules are loaded so
I know it may sound weird, but run **alsamixer** and make sure that neither Master nor PCM say "MM" (Mute)... Sometimes the gnome interfaces don't show every slider by default and one of them may be muted.  Happened to me once, fought with it for two days before realizing it was something stupid like that :D.

---

### Post by DaMasta on 2005-06-20
[QUOTE=intangible]Looks like all the right modules are loaded so
I know it may sound weird, but run **alsamixer** and make sure that neither Master nor PCM say "MM" (Mute)... Sometimes the gnome interfaces don't show every slider by default and one of them may be muted.  Happened to me once, fought with it for two days before realizing it was something stupid like that :D.[/QUOTE]
That was it. Thank you very, very much. =D>

---

