---
title: "How can I make my touchpad more smooth?"
date: 2011-06-20
forum: Hardware
---

### Post by Vostrocity on 2011-06-20
For the most part, my laptop touchpad works well. But a few minor issues:
[LIST=1]
[*]When I do a big scrolling swipe down my touchpad, then press the Ctrl key, the screen would zoom out. Obviously the touchpad is trying to do momentum but it's annoying whenever because the screen zooms in and out whenever I try to use a Ctrl shortcut right after scrolling. How do I disable that?

[*]The scrolling behaves as if there are mouse wheel indents. How do I get smooth scrolling?

[*]This is more of a wish.. has anyone built a Linux driver that would allow true momentum scrolling like on newer Macs?
[/LIST]

---

### Post by tgalati4 on 2011-06-20
man xset

If your trackpad was made by Synaptics then there are some utilities:

apt-cache search synaptic

sudo apt-get install gsynaptics
gsynaptics

---

