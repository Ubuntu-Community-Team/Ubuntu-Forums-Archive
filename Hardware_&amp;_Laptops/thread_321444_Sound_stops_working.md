---
title: "Sound stops working"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by YbJ on 2006-12-18
Hello.  I'm not sure whether this should be in the "Hardware & Laptops" section, but since I have a laptop here goes nothing.

Most of the time, the sound works fine.  Xmms, mplayer, and any other program that should output audio does.  However, sometimes after I open my laptop, causing it to come out of suspended mode (I have it set to suspend when I close it), the sound just stops working.  I have no output from speakers or the headphones I often use.  I have no explanation for this; Volume Control shows everything unmuted and at normal levels.  It's very annoying.  Fortunately, a reboot always fixes the problem, but I'm certainly not setting any records for the longest up-time of a laptop doing this.

I'm using Ubuntu 6.06 Dapper on a Lenovo Thinkpad T60.
The following was done when the sound doesn't work.

"lsmod | grep snd" gives:

snd_hda_intel 18964  1
snd_hda_codec 157616  1 snd_hda_intel
snd_pcm_oss 53664  0
snd_mixer_oss 18688  1 snd_pcm_oss
snd_pcm 89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer 25220  1 snd_pcm
snd 55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore 10208  1 snd
snd_page_alloc 10632  2 snd_hda_intel,snd_pcm

"lspci -v" gives (among other things):

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
Subsystem: Lenovo: Unknown device 2010
Flags: bus master, fast devsel, latency 0, IRQ 66
Memory at ee240000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <available only to root>

I have no idea what to do or what is causing the problem.  Help please?

---

### Post by xyz on 2006-12-19
Try running
```
alsamixer
```
in a terminal and check volume levels/settings using the arrows.
Maybe...

---

### Post by YbJ on 2006-12-19
Running alsamixer tells me the same things as Volume Control.  I have tried before when the problem occurred, and nothing was muted and volumes were as they should be (Master = 62, PCM = 61, everything else = 0).

I now have a working system and can confirm the output from lsmod and lspci to be the same as they were above.

---

### Post by Lego on 2006-12-20
I have the same problem with the audio, even though I don't have a laptop. ](*,)

---

### Post by aalami90 on 2008-03-16
heey
so did u find a solution to that problem?
cause i have it too

---

