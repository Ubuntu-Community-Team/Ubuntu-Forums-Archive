---
title: "Laptop sound promblem still"
date: 2009-12-26
forum: Hardware
---

### Post by AllanP on 2009-12-26
I know there are numerous other sound problem threads, but I have a couple of curious responses to terminal commands:

[U]allan@allan-laptop:~$ killall pulseaudio
allan@allan-laptop:~$ sudo alsa force-reload[/U]
[sudo] password for allan: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/allan/.gvfs
      Output information may be incomplete.
Terminating processes: 14660lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/allan/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/allan/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/allan/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-pcm-oss snd-mixer-oss snd-hwdep snd-seq-dummy snd-pcm snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-pcm-oss snd-mixer-oss snd-hwdep snd-seq-dummy snd-pcm snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
_allan@allan-laptop:~$ pulseaudio -D_
E: main.c: Daemon startup failed.

Any ideas where to go from here? I've installed the latest Alsa. I have sudo gedit /etc/modprobe.d/alsa-base.conf and added "options snd-hda-intel model=laptop". Am running out of things to try.

---

