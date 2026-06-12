---
title: "No sound is Zsnes"
date: 2008-10-22
forum: General Help
---

### Post by Animal_Allen on 2008-10-22
Sound works fine on everything else, none in Zsnes though.  Tried "zsnes -ad sdl"  but terminal gives following output:

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

Anyone know why Zsnes might be nixing my sound?

Ubuntu 8.04.1

"ALSA lib pcm_dmix.c:874: (snd_pcm_dmix_open) unable to open slave"

stupid emoticons...

---

### Post by shaggy999 on 2008-10-22
This is a known bug. Let me find the bug report...

Here it is: [https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/188567](https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/188567)

The general consensus is that you should do the following:

```

sudo apt-get install libsdl1.2debian-oss
pasuspender -- zsnes -ad auto

```

If that doesn't work try replacing 'auto' with 'sdl'.

---

