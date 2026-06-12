---
title: "no sound through 3.5mm jack"
date: 2013-09-16
forum: Hardware
---

### Post by arnold_layne2 on 2013-09-16
HP DV6 6121tx

If I plug anything into my 3.5mm jack, be it headphones or full speakers, the 'mute' light on my keyboard lights up. Pressing the mute button still toggles between the Mute and Unmute state in Ubuntu, but the red light stays lit regardless, and there is no output at all. 

[B]I figured out a way to fix this, in Sound settings, after plugging anything into the jack, the 'Connector' option changes to 'Headphones'. Changing it back to 'Speakers' fixes the issue.
[/B]
I have to do this every time I plug in my headphones/speakers so it's kind of annoying. 

Any clue how to fix this once and for all?

---

### Post by tgalati4 on 2013-09-16
The behavior of the jack is controlled by scripts that are run when certain events are detected.

First, figure out what sound module you are running.  Open a terminal:

```
lsmod | grep snd
```

It might look like:

tgalati4@Mint14-Extensa ~ $ lsmod | grep snd
snd_hda_codec_realtek    78147  1 
snd_hda_intel          33492  2 
snd_hda_codec         134213  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78921  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm

To see if there are any switches:

```
modinfo snd_hda_intel
```

There are some configuration settings in /etc/pulse.

There is a lot of troubleshooting procedures here:  [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

On switching audio devices:  [http://askubuntu.com/questions/4055/audio-output-device-fast-switch](http://askubuntu.com/questions/4055/audio-output-device-fast-switch)

[http://askubuntu.com/questions/14077/how-can-i-change-the-default-audio-device-from-command-line](http://askubuntu.com/questions/14077/how-can-i-change-the-default-audio-device-from-command-line)

Take careful notes of what you have tried and what finally works and post the results.

---

