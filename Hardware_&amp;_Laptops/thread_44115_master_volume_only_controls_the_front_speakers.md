---
title: "master volume only controls the front speakers"
date: 2005-06-24
forum: Hardware &amp; Laptops
---

### Post by dancnpete on 2005-06-24
Perhaps I'm missing something here that I'm not meant to understand. I appologize if this should be in the software section, but I wasn't sure where to put it.

PROBLEM:
using nVidia soundstorm drivers I can only get sound out of the rear speakers if I duplicate the fronts. However when I now try to contol the master volume it only adjust the front speakers while the rears blast out sound. Is there a way to link the surround controls to the master?

---

### Post by skoal on 2005-06-24
Have you tried adjusting the rear speaker settings as well?  See attached picture (with the red arrows).  Try adjusting those 3 (Wave Center, Wave LFE, and Wave Surround) to your liking.

* I'm not familiar with the "soundstorm" drivers.  Is that an alsa driver?  Anyway, instead of duplicating channels, try adjusting those 3 channels first (if you can).

\\//_

---

### Post by dancnpete on 2005-06-24
it says it is using the alsa mixer, I do not see  (Wave Center, Wave LFE, and Wave Surround)
on my mixer I have under the playback tab:
Master, 3d control, PCM Surround, Center, LFE

I have a 4 speaker setup so the center and lfe do nothing, what makes no sense is that the master does not control all of the sound. I don't have a front speaker control either but that is a minor annoyance I can live without that.

---

### Post by dancnpete on 2005-06-26
Is this a universal problem or am I the only one whose experienced this? :confused:

---

### Post by dancnpete on 2005-06-26
not a solution but a workaround. if I can control the volume of both front and rears if I  control them through the programs themselves. Now all that is left is to convince my brain that master means front

---

### Post by ingomueller.net on 2007-01-11
Hi!

I had a similar problem one month ago and have spent a lot of time in its solution. As I stumbled upon this post, probably others will, so I'll post the link to a howto I wrote:

[http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume](http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume)

I hope this helps someone...

Ingo

---

### Post by Skybinary on 2008-01-06
Hi yall,

I have had alot of probs with my audio from scratch, ie: muted audio on install :(.

But like dancnpete i dont understand why if i change the mixer control on the top panel to mute 'master surround' and i use mmkeyboard to mute, it only affects 'master',

For some reason when 'master' is muted i still get audio untill i mute 'master surround'.

Confused uhuh, i wont mind using a fudge or workaround, if it were easy enuff for a thicko like me to understand.

---

