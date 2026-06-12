---
title: "Flaky Audio"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by hauger on 2007-10-20
Hi everyone.

So I'm trying patiently to get 7.10 running nicely on my HP DV2000 laptop.  There are definite issues, however, there's one that's a real pain in the butt.

Sound.

I've had this issue before with other releases and on other hardware, but I've never solved it.  See, the sound hardware has been properly identified and does work, but seems at best to have about a 25% success rate.  About 3/4 of the time starting up, although everything looks fine, I get no sound at all (regardless of how many times I restart the audio system), and the other 1/4 of the time I actually get audio.

Is there any way to maybe get the sound to run, say, all of the time, or do I just have to accept this?  Thanks for any tips/advice you can offer.

---

### Post by hauger on 2007-10-21
Okay, here's an update.  I've read just about everything I could find on this issue, but no one seems to be suffering the same exact problems.  Anyways, here's what I have so far:

Installed MP3 support and played a bunch in Amarok.  Everything seems normal, visualization is running nicely.  This makes me believe that Amarok, as far as it's concerned, is talking to a working sound system.

Alsamixer run from the shell shows all settings normal (not muted, all turned way up).

Tried running sound programs from Root.  No sound there either.

Output of lspci -v:

[I]00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
[/I]
Output from lsmod | grep snd:

[I]snd_hda_intel         263712  2
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
[/I]

Output from aplay --list-devices:
[I]card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/I]

I've seem posts talking about recompiling ALSA from source, but I'm hesitant to do so, since the sound system does sometimes (but not often at all) work, and I really don't want to mess things up worse than they are (a real possibility). So.....HELP...PLEASE.

Thanks, 
Rob.

---

### Post by hauger on 2007-10-22
UPDATE:  Ended up filing a bug report.  Still looking for any help any one can offer.

Thanks.

---

### Post by hauger on 2007-10-22
*BUMP*

Still looking for some kind of help, although at this point I'd also settle for some general sympathies.  Anyone?  Anyone?

---

### Post by hauger on 2007-10-25
meh, never mind.  I'll figure it out on my own.

---

