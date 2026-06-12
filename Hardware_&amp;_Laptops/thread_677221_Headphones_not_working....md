---
title: "Headphones not working..."
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by bcardarella on 2008-01-24
Let me preface this with the following:

1.) Yes the volume is up
2.) Yes the headphones do work

I have a new laptop that has, according to my manuf. (Sager) the Built-in 8ch Azalia Sound System.

External sound works just fine.
I have no 'headphones' meter in the volume control panel. When I enable 'headphones' in the Preferences a new tab appears called "Switches" and 'headphones' is checked.

According to *lspci* I have:
```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

and after doing *lsmod | grep snd* I get:

```

snd_hda_intel         263712  5 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

```

Any thoughts? This is really annoying as I usually listen to music at work but cannot without headphones.

---

### Post by bcardarella on 2008-01-24
Oh yeah, there is another audio out jack but it is digital S/PDIF so my headphones don't plug into it... and I don't have anything that I can plug it into to test. So for me it's really just the headphone jack.

---

### Post by bcardarella on 2008-01-24
I've done some more digging. If I run the alsamixer command line app I get the following information about the headphones:

Card: HDA Intel
Chip: Realtek ALC883
View: [Playback] Capture All
Item: Headphone


In the column for the headpone it is just a box with '00' listed. There is no column above the box to signify a volume amount. And there are no Left/Right channel numbers below the box to signify each channel. I can Mute 'MM' the headphones but this doesn't really do anything considering there is no sound coming out anyway.

Still looking.... I'm going to continue documenting this here even if nobody has any help... just incase someone else has the same issue.

---

### Post by bcardarella on 2008-01-24
I have found the solution. I came across someone else on the Alsa-User mailing list who was having similar issues. I emailed him and this was a volume solution after all. Only the problem is that the 'Surround' meter needs to be unmuted and turned up: Original email...

I hope this saves someone else some headaches.


>>>>>>>

Hello,
yes I have :)

In fact it's was working from the beginning but the volume control of 
the headphone was 0% and on my laptop the volume to control the 
headphone is called "Surround" and not "Headphone".

Try all the controlers on 'alsamixer' while listening music to find the 
right volume control :)

See you,
Guillaume.
Ps: I'm not suscribed yet on the alsa list.
---
Brian  a écrit :
> I came across your posting on the Alsa-User mailing list from Sept. 2007
> about no headphone audio with your Realtec ALC883 HDA Intel sound card.
> I'm having the exact same issue and was wondering if you ever found a
> solution? Thanks for any help.
> 
> - Brian
>

---

