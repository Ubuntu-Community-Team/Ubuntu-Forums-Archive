---
title: "OSS: Horrible Distortion In Right Channel"
date: 2008-11-07
forum: General Help
---

### Post by Mark76 on 2008-11-07
I've eliminated the amplifier and cable as possible causes, so it's down to either the software (oss) or my soundcard (a Nvidia HDA (MCP61)). Sadly I don't know how to change back from OSS to ALSA, and the instructions I tried to follow are confusing and for Hardy (I upgraded).

---

### Post by Mark76 on 2008-11-07
I tried the other outputs on my soundcard to make sure that wasn't the problem and got exactly the same thing on each. But only if I set it to the Front channel.

So it's something to do with that.

Help :(

---

### Post by Mark76 on 2008-11-08
Okay. It's definitely something to do with OSS in Intrepid. I ran a live session of Ubuntu from CD and the sample audio played back fine.  I also did some more tests using osstest -V. The results are:

Left plays back at reduced volume
Right plays back at clipping level (you can hear artifacts), but you can still hear the music.

I also discovered that if I let the tests (normal and -V) run to the end that, as long as the inout is set to Front I also get audio from spdif-out. This is normal on both channels regardless of the test being run.

---

