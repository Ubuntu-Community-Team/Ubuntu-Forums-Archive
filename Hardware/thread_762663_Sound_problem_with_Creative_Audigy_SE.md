---
title: "Sound problem with Creative Audigy SE"
date: 2008-04-22
forum: Hardware
---

### Post by Hulfok on 2008-04-22
Hey there!
I have a bit problem with my sounds. First of all only one program at time can use my sounds. Meaning if i listen to music with XMMS i can't hear any sounds from games, videos etc etc. I had that prob sometimes, but now i just can't solve it:( Second of all my ventrilo isn't working. I can use it but it says that *""No mixers available"* and *"Unable to activate DirectSound for selected device".* Command *lspci -v* gives out this:
```
01:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 32, IRQ 22
        I/O ports at bc00 [size=32]
        Capabilities: <access denied>
```
So clearly ubuntu recognizes my sound card. Command *lsmod | grep snd* prints this:
```
snd_rtctimer            4384  0 
snd_ca0106             34720  1 
snd_ac97_codec        100644  1 snd_ca0106
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ac97_bus                3200  1 snd_ac97_codec
snd_page_alloc         11400  2 snd_ca0106,snd_pcm

```
Even a tiny advice will help me to figure out this problem:)
Feel free to ask more infoes!
Thanks.

---

### Post by HolyAvenger on 2008-04-23
I'm having the same problem. Weird thing is, until yesterday I didn't. I thought I reboot might fix it (it did last time) but now it's not solving anything. (Not that rebooting has a magical spell or someting anyways ...)

---

### Post by dcn on 2008-04-26
I've the same problem too.
lspci displays the name of sound card but then no mixer available :(

---

### Post by dcn on 2008-04-26
I've got some news.

When I first installed 8.04 I had a problem with my Nvidia GPU and then installed the proper driver. This driver required to install the i386 kernel instead of the "generic" that comes at first.

Now I retried to use the "generic" kernel and the sound is ok!
In fact I remembered that at my first boot the sound was ok (quiet because my headphones were close to the minimum). Then I went to the 386 to use the Nvidia driver.

But now that I come back to the generic kernel the sound is ok and the Nvidia driver works too!

I hope it will help you.

---

