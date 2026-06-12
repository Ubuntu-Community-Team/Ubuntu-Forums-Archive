---
title: "synaptics mouse driver steals other mice"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by noisesmith on 2008-04-08
The synaptics mouse driver grabs other mice, aside from the device I tell it to use. I will admit that I am not the normal usage case: I wrote a demon to send per-device open sound control events controlled by multiple mice, for input to software synthesizers. I want to be able to rock out on the five other mice on my system without moving or clicking the X11 cursor. If I use the regular "mouse" driver, only the synaptics device controls the pointer, like I would expect, if I use the "synaptics" driver, events from all of the mice get grabbed. Is this a configuration issue? Am I just being lazy? Maybe I should rewrite the synaptics driver, with all those other bugs people are getting with it anyway.

---

