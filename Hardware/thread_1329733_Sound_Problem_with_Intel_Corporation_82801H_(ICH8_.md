---
title: "Sound Problem with Intel Corporation 82801H (ICH8 Family) HD Audio Controller"
date: 2009-11-17
forum: Hardware
---

### Post by d3ngar on 2009-11-17
Hey,

I have the most annoying sound problem since upgrading to 9.10. Sometimes my sound adapter doesn't get recognised, but then other times it comes on fine at start up.

I have been able to force alsa to restart and then all is good:
[INDENT]sudo alsa force-reload[/INDENT]

(screenshots attached)

But I do get some weird message, sometimes, which I don't understand:
```

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dengar/.gvfs
      Output information may be incomplete.
Terminating processes: 1313lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dengar/.gvfs
      Output information may be incomplete.
 3151lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dengar/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dengar/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dengar/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```

What's the fuse deamon and does anyone have a cure?

---

### Post by d3ngar on 2009-11-18
OK, bump?!

---

### Post by escozul on 2009-11-19
It seems that I get the same thing too. When restarting ALSA everything works fine. However some times (or all the time - not sure) seems that I have sound. It used to work good when I first installed everything. I followed the instructions found here: [http://ubuntuguide.org/wiki/Ubuntu:Karmic]("http://ubuntuguide.org/wiki/Ubuntu:Karmic") to add extra decoders and stuff. since then I get the sound on and of and on again thing. Hope somebody has a solution to this. It seems to me though that my problem is not random but permanent. I need to restart ALSA all the time.

---

### Post by d3ngar on 2009-11-24
I'm just going to bump this one more time...

This problem still exists for me...

---

