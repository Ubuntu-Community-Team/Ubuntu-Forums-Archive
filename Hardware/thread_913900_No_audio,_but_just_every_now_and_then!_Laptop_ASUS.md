---
title: "No audio, but just every now and then! Laptop ASUS F3Ja - ICH7 Family sound card"
date: 2008-09-08
forum: Hardware
---

### Post by manolomanolo on 2008-09-08
**lspci -nn | grep -i audio**
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)

I don't know why it can happen that Ubuntu reproduces no audio. The problem presents every now and then. I mean it can happen that when I boot Ubuntu can play mp3, audio streams, system sounds etc. But it can also happen that booting Ubuntu gaves me no sound at all. In this case I try using different audio players, open some youtube video, some divx but no way to hear any sound.

In both cases Ubuntu gives me no audio at startup, I mean when just ending up loading the operating system nor when shutting it down.

Is there something I can do to see if there's some kind of problem visible in case of no audio?

Now, for example, I have this kind of problem and made the tests of above, I also suppose this could help:

manolo@manolo-laptop:~$ **lsmod | grep intel**
snd_hda_intel         359192  0 
snd_hwdep              10628  1 snd_hda_intel
snd_pcm                78852  3 snd_hda_intel,snd_pcsp,snd_pcm_oss
intel_agp              25492  0 
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
agpgart                34760  2 fglrx,intel_agp
snd                    57124  14 snd_hda_intel,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_pcsp,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
manolo@manolo-laptop:~$ **lsmod | grep snd**
snd_hda_intel         359192  0 
snd_hwdep              10628  1 snd_hda_intel
snd_seq_dummy           4996  0 
snd_seq_oss            35456  0 
snd_pcsp               13600  1 
snd_seq_midi            9504  0 
snd_pcm_oss            42528  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_rawmidi            25888  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_pcm                78852  3 snd_hda_intel,snd_pcsp,snd_pcm_oss
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
snd_timer              24964  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    57124  14 snd_hda_intel,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_pcsp,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
manolo@manolo-laptop:~$ **lsmod | grep alsa**
manolo@manolo-laptop:~$ 

I think I'll now restart the system and run those commands back again, in case of hearing some audio and compare it with the previous output.

Stay tuned!

---

### Post by manolomanolo on 2008-09-08
Now audio works properly. That's the output of those previous commands.

manolo@manolo-laptop:~$ **lsmod | grep intel**
snd_hda_intel         359192  7 
snd_hwdep              10628  1 snd_hda_intel
snd_pcm                78852  4 snd_hda_intel,snd_pcm_oss
intel_agp              25492  0 
snd                    57124  21 snd_hda_intel,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
agpgart                34760  2 fglrx,intel_agp

manolo@manolo-laptop:~$ **lsmod | grep snd**
snd_hda_intel         359192  7 
snd_hwdep              10628  1 snd_hda_intel
snd_seq_dummy           4996  0 
snd_seq_oss            35456  0 
snd_seq_midi            9504  0 
snd_rawmidi            25888  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm_oss            42528  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                78852  4 snd_hda_intel,snd_pcm_oss
snd_timer              24964  4 snd_seq,snd_pcm
snd                    57124  21 snd_hda_intel,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
soundcore               8800  1 snd

manolo@manolo-laptop:~$ **lsmod | grep alsa**
manolo@manolo-laptop:~$

What can I do?
Thanks for your time.
Regards.

---

### Post by manolomanolo on 2008-09-13
My problem persist. Any suggestion, please?
Regards.

---

