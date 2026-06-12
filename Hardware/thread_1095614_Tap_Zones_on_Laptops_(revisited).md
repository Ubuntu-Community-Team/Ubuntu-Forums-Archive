---
title: "Tap Zones on Laptops (revisited)"
date: 2009-03-13
forum: Hardware
---

### Post by brownbat on 2009-03-13
I'm looking over the info [here]("http://ubuntuforums.org/showthread.php?t=518826") on setting up tap zones on my laptop. I've read through the different xorg.conf options found under the synaptics manual, but when I went to edit my xorg.conf, I noticed I had section with a mouse driver, but no touchpad section (even though gsynaptics seems to be running things ok).

Should I:
a) delete the mouse section and add a touchpad or device a section?
b) change the driver in that section to "Synaptics"?
c) install the synaptics driver some other way?

I have gSynaptics installed, should I ditch that and just configure everything in the same place, under xorg.conf, say?

---

