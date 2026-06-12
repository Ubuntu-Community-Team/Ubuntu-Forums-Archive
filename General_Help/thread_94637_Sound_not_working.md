---
title: "Sound not working"
date: 2005-11-24
forum: General Help
---

### Post by outsider787 on 2005-11-24
Well, I'll start off by saying that I'm a total noob. (gotta start somewhere)

I installed ubuntu on a spare desktop PC I had, which has a SB Live card in it.
After install, sound is not working.
I know this is vague. What kind of info do I need to post here for you guys to be able to help me sort this issue out?

---

### Post by charle97 on 2005-11-24
i had the same problem a few days ago.

type into the terminal:

alsamixer

a simple interface with bars should appear.  using the left or right arrow keys, i think, go to each bar. use the up and down keys to fill the bar to the desired level.  i just maxed them all.  i have no idea what they do, but i got sound.

---

### Post by outsider787 on 2005-11-24
Let me be a little more specific in my problem.

In "system > Administration > Device Manager" I can see that the OS recognized a SB Live! EMU10k1
However, if go to "System > Preferences > Sound" there is no option available to select under "Default sound card"
And when I try a test using ANY of the sound systems (ALSA, OSS..) in 'Multimedia Systems Selector',  I get a "Failed to construct pipe line for selected sound system"

Are there specific drivers I need to install for this run-of-the-mill card?

Am I missing something that is really obvious?

---

### Post by charle97 on 2005-11-24
do you have all of the alsa packages installed?

---

### Post by az on 2005-11-24
Try this for older sound cards:
[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

---

### Post by nszabolcs on 2005-11-24
lspci | grep audio

lsmod | grep snd

alsamixer

sudo killall esd

---

### Post by outsider787 on 2005-11-24
[QUOTE=nszabolcs]lspci | grep audio
[/quote]
0000:00:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
> 
lsmod | grep snd

snd_emu10k1_synth       6528  0
snd_emux_synth         31744  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6528  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                44688  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1            96772  1 snd_emu10k1_synth
snd_rawmidi            22816  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         72188  1 snd_emu10k1
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8608  2 snd_emux_synth,snd_emu10k1
snd                    48644  13 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9184  1 snd
> 
alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
> 
sudo killall esd
esd: no process killed

so it seems the drives is loaded into the kernel... what gives?

---

### Post by az on 2005-11-24
[QUOTE=outsider787]
After install, sound is not working.
I know this is vague. What kind of info do I need to post here for you guys to be able to help me sort this issue out?[/QUOTE]

Pardon the reall bumb question, but, is your sound muted?  Is there a little "x" on the bottom of the speaker on the top-right of your screen?  If you double-click it, you get to see all the sound sliders and can raise the master or pcm volume and unmute them, too.

If you have no speaker on your top-right, then that is not your problem.

---

### Post by outsider787 on 2005-11-24
No dumb questions... 
:)
There is a little "x" besides the speaker, however, when I doubleclick the speaker it tells me "No volume controls and\or devices found"

---

