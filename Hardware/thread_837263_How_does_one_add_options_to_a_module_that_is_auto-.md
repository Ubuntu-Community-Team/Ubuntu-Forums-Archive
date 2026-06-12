---
title: "How does one add options to a module that is auto-inserted on boot?"
date: 2008-06-22
forum: Hardware
---

### Post by dev.urandom on 2008-06-22
I've decided to compile kernel 2.6.25.7 due to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/242006](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/242006)

The only problem is that I can't get the sound to work automatically.

My audio uses the module 'snd-hda-intel' with the option 'model=5stack'

if I do : "rmmod snd-hda-intel; modprobe snd-hda-intel model=5stack" before starting any audio apps, I can get sound.

So I've tried adding "options snd-hda-intel model=5stack" to /etc/modprobe.d/alsa-base. That didn't work. Then I tried adding it to /etc/modprobe.d/options. That didn't work as well. Finally, I tried adding "snd-hda-intel model=5stack" to /etc/modules, and that didn't work as well.

How can I make this work?

---

