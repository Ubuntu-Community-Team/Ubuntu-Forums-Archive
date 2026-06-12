---
title: "Touchpad settings"
date: 2009-12-16
forum: Hardware
---

### Post by Agent9 on 2009-12-16
How do I get access to the touchpad settings for my laptop? When I go to Applications -> Settings -> Mouse I do not have a touchpad tab. I've tried to install gsynaptics and tpconfig but it still doesn't show up. Thanks.

---

### Post by Agent9 on 2009-12-16
bump

---

### Post by joeclarkia on 2009-12-20
I have the same problem -- no Touchpad tab.  Asus U80A laptop.  There must be a bug involved, but after some searching haven't found any clear diagnosis.

---

### Post by Agent9 on 2009-12-21
> **joeclarkia said:**
> I have the same problem -- no Touchpad tab.  Asus U80A laptop.  There must be a bug involved, but after some searching haven't found any clear diagnosis.
I'm glad it's not just me. What have you tried so far?

---

### Post by Some Penguin on 2009-12-21
Synaptics issue?

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

For what it's worth -- a friend of mine set up Ubuntu on an ancient laptop.  The touchpad was initially never recognized, until the SHMConfig bit was fixed -- then, it was recognized only occasionally.  What I found when researching this was references to a bug in the 2.6.31 version of the kernel.  See 

[http://bugs.gentoo.org/287019](http://bugs.gentoo.org/287019)

for some discussion, for instance.

If that's what you're running into, you may be able to install the kernel from Lucid Lynx as this particular bug is supposed to be fixed in 2.6.32 upstream.

---

### Post by Agent9 on 2009-12-21
> **Some Penguin said:**
> Synaptics issue?

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

For what it's worth -- a friend of mine set up Ubuntu on an ancient laptop.  The touchpad was initially never recognized, until the SHMConfig bit was fixed -- then, it was recognized only occasionally.  What I found when researching this was references to a bug in the 2.6.31 version of the kernel.  See 

[http://bugs.gentoo.org/287019](http://bugs.gentoo.org/287019)

for some discussion, for instance.

If that's what you're running into, you may be able to install the kernel from Lucid Lynx as this particular bug is supposed to be fixed in 2.6.32 upstream.
Thanks for the links.

My touchpad works, I just can't access the options through the GUI. For example, I would like to turn off tapping.

The wiki is where I got the information about installing the gsynaptics package. Still no tab. Unless the feature is stored somewhere else?

I can change the settings manually from the terminal but I didn't want to have to modify any scripts if I don't have to.

---

### Post by sumi76 on 2010-02-03
Hi!

In case you're still looking for the answer:
you should be able to turn off tapping in the gsynaptics window.
I'm quite new to Ubuntu myself, so no clue how far xubuntu works, looks differently than ubuntu, but here's how is it working for me:
Install, check System > Preferences, there should be a new entry called Touchpad. This opens the gsynaptics GUI.
Otherwise press Alt+F2 > type gsynaptics and run.

Hope it helps!

---

