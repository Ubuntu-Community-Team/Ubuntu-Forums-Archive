---
title: "No Sound 8.10"
date: 2008-11-01
forum: General Help
---

### Post by Robbyx on 2008-11-01
I have completed the upgrade and have it working after a lot of problem due to insufficient guidance in the option boxes in the upgrade. I probable chose the wrong options.

I now find that I have no sound. It is not muted. I had it working in Hardy. I would appreciate help to get it working.

---

### Post by Robbyx on 2008-11-01
Does anyone have a solution?

---

### Post by laplace/d on 2008-11-02
here's something that did it for me:
[http://onlyubuntu.blogspot.com/2008/11/fix-for-no-sound-issue-in-ubuntu-810.html](http://onlyubuntu.blogspot.com/2008/11/fix-for-no-sound-issue-in-ubuntu-810.html)

hope it works!

---

### Post by Robbyx on 2008-11-02
Thank you for your suggestion. It did not work for me. Are you able to see why?

> robin@robin:~$ sudo killall pulseaudio
[sudo] password for robin: 
robin@robin:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/robin/.gvfs
      Output information may be incomplete.
Terminating processes: 6688lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/robin/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/robin/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/robin/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
robin@robin:~$ 


---

### Post by laplace/d on 2008-11-02
i really don't understand that, i'm new to ubuntu, and i've been struggling since i upgraded to 8.10  . this is what i get

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/simon/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/simon/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-via82xx snd-ac97-codec snd-mpu401-uart snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-via82xx snd-ac97-codec snd-mpu401-uart snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

it's pretty similar...i don't know that much but maybe it is that module  snd-ac97-codec

---

### Post by der_joachim on 2008-11-03
The link in LaPlace's post worked for me. Thanks.

---

### Post by Robbyx on 2008-11-07
I still do not have sound working and that link did not work for me.

---

### Post by AlaskanAdmiral on 2008-11-09
I'm having some issues as well with sound. RobbyX, what are you using to test whether sound is working for you or not?

The startup sound for ubuntu doesn't work for me, it just produces a light clicky sound, and firefox flash doesn't produce sound... and the test buttons for ALSA and PulseServer in the System>Prefs>Sound window produce no sound.  Alsa and Pulse will give me the clicky noise at first but thats it. then when i try that solution, alsa and pulse just give me nothing but errors.

Right now MP3's work, however. I have not tested to see if MP3's work without the killallpulse/reloadalsa tactic.

---

### Post by Robbyx on 2008-11-09
> **AlaskanAdmiral said:**
> I'm having some issues as well with sound. RobbyX, what are you using to test whether sound is working for you or not?

The startup sound for ubuntu doesn't work for me, it just produces a light clicky sound, and firefox flash doesn't produce sound... and the test buttons for ALSA and PulseServer in the System>Prefs>Sound window produce no sound.  Alsa and Pulse will give me the clicky noise at first but thats it. then when i try that solution, alsa and pulse just give me nothing but errors.

Right now MP3's work, however. I have not tested to see if MP3's work without the killallpulse/reloadalsa tactic.

Nothing would come out of my headphones. I have switched to OSS. I have tried to install oss4 but the instructions do not work for me. I could not follow them without error. However I do have oss3? working and so can hear sound at present.

---

