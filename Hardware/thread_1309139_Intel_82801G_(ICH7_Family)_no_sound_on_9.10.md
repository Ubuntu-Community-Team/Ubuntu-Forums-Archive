---
title: "Intel 82801G (ICH7 Family) no sound on 9.10"
date: 2009-11-01
forum: Hardware
---

### Post by Tryfon on 2009-11-01
Hi, 
I installed 9.10 yesterday but the sound is not working. In Sound Preferences in the Output tab I only get a Dummy Output. Help please, it's really frustrating not to have sound while everything else works perfectly!

---

### Post by Tryfon on 2009-11-01
Ok, solved, just follow the instructions here: [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by wareagle on 2009-11-02
I had the same problem with my HP Compaq nc8430.

That thread worked for me but was very confusing :confused:.

I basically tried pasting the options that appeared most likely to work in my '/etc/modprobe.d/alsa-base.conf' file, which was:

```
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1
```

When I ran 'pulseaudio -D' I got this message:
```
E: main.c: Daemon startup failed.
```
but the sound started working. :D

---

### Post by wareagle on 2009-11-02
Also got some weird errors when running c'sudo alsa force-reload'
```

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cbolduc/.gvfs
      Output information may be incomplete.
Terminating processes: 1788 2501lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cbolduc/.gvfs
      Output information may be incomplete.
 4139lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cbolduc/.gvfs
      Output information may be incomplete.
 4166lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cbolduc/.gvfs
      Output information may be incomplete.
 4183lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cbolduc/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 4200lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cbolduc/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 4218(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cbolduc/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 4218(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-si3054 snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```

---

