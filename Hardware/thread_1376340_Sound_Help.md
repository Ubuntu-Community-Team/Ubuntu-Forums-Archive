---
title: "Sound Help"
date: 2010-01-09
forum: Hardware
---

### Post by mmeisam on 2010-01-09
I have tried following the sound troubleshooting guide but I still cannot get my audio working. It was working just fine up until a few days ago and then it suddenly stopped without me doing anything. I am by no means an expert with linux as a matter of fact I would consider myself a noob. Here are the outputs from their respective commands:

```
meisam@meisam-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
aplay: device_list:232: control open (0): No such file or directory

```
I have tried googling libasound_mofile_conf_pulse.so but i couldnt find anything useful.

```
meisam@meisam-laptop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/meisam/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/meisam/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-pcm snd-page-alloc snd-mixer-oss snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device (failed: modules still loaded: snd-hda-codec-conexant snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-pcm snd-page-alloc snd-mixer-oss snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

```

Alsa information can be found at [http://www.alsa-project.org/db/?f=2a295066ef662d7a07c03d9ff90e98139789c5f4](http://www.alsa-project.org/db/?f=2a295066ef662d7a07c03d9ff90e98139789c5f4)

```
meisam@meisam-laptop:~$ pavucontrol
pavucontrol: error while loading shared libraries: libvorbisfile.so.3: cannot open shared object file: No such file or directory

```
I'm not sure how libvorbisfile.so disappeared. I'm pretty sure something is screwed up big time but have no idea what it is any help would be appreciated.

---

### Post by mmeisam on 2010-01-09
bump

---

