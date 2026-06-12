---
title: "ALSA vs OSS - how can I tell, and switch to ALSA?"
date: 2005-01-14
forum: Hardware &amp; Laptops
---

### Post by dmerrill on 2005-01-14
Hello there -
Thanks in advance for the great forum advice! I am running Hoary Hedgehog on my Thinkpad T40 (upgraded from Warty to try to get a few new features), and am now having some audio problems. When I open up Audacity - which I usually use for audio recording - it pops up a box that says "There was an error initializing the audio i/o layer. You will not be able to play or record audio. Error: Host Error"

Any thoughts on this? (some details below). I'd like to use Alsa, but I don't know how to determine whether I'm running ALSA or OSS. I suspect that it's OSS based on the output of lsmod (see below) - and if that's the case, I'd like to switch over. In the past I've used alsaconf to configure Alsa, but I can't seem to find it - even though I have the alsa-utils package installed... any ideas would be greatly appreciated.
thanks,
David Merrill

dmerrill@dmerrill-T40:~ $ ls -lah /dev/dsp
crw-rw----  1 root audio 14, 3 2005-01-14 01:47 /dev/dsp

dmerrill@dmerrill-T40:~ $ groups
dmerrill adm dialout cdrom floppy audio video plugdev lpadmin scanner

dmerrill@dmerrill-T40:~ $ lsmod | grep snd
snd_intel8x0m          17220  0
snd_intel8x0           29984  2
snd_ac97_codec         64608  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  7 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  3 snd_intel8x0m,snd_intel8x0,snd_pcm

---

### Post by LB06 on 2005-01-14
The snd_ part indicates that it is an alsa module. Can't help you with the recording issue, unfortunately.

---

### Post by wulf on 2005-01-15
Try turning off esd before running audacity or running it from the command line. Either seem to allow it access to /dev/dsp. I don't fully understand why but that seems to work (a quick search on "audacity esd" will show other threads with this info).

Wulf

---

