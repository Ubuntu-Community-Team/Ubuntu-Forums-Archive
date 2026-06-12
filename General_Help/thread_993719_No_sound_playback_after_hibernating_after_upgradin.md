---
title: "No sound playback after hibernating after upgrading to Intrepid Ibex 8.10."
date: 2008-11-26
forum: General Help
---

### Post by kaoskorruption on 2008-11-26
I'm on a Gateway T-6836 with recently upgraded Intrepid Ibex (8.10). The sound controller is HDA Intel (Alsa mixer) and SigmaTel STAC9205 (OSS Mixer). Sound playback worked perfectly before I upgraded to Intrepid. Sound playback also works perfectly when I turn the computer on or restart it - until I hibernate. Once I resume from hibernation, the sound fails. Interestingly, I not only do not hear any sound, but it won't PLAY, meaning that in Rhythmbox and Pandora for example, the progress bar won't even move forward, despite that fact that it is in play mode. No other sounds work either.

The only way that I can get it to to work, which only works sometimes, is to go to the command line and exectute "sudo /sbin/alsa force-reload". The result is this:```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/chris/.gvfs
      Output information may be incomplete.
Terminating processes: 5948 6042 7812lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/chris/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/chris/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/chris/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
```
What then happens is the Volume Control applet shows that the volume is muted. The "Front" volume became turned all the way down when I exectued the command, as seen when I right click "Open Volume Control" on the applet. If I turn this volume back up all the way, I can hear again. But strangely, the applet still shows that it is muted. Also, if I right click "Preferences, nothing comes up." Of course, all of this is true only after I hibernate and then execute that command - before I hibernate everything works perfect.

What in the world can I do to fix this problem?

Many thanks!

---

### Post by kaoskorruption on 2008-11-27
Bump.

---

### Post by linux4me on 2008-11-28
I just did an upgrade from AMD 64-bit 8.04 to 8.10 and found that after resuming from suspend I am having a similar problem with Rhythmbox. I pause playback and go into suspend, then when I resume and click play on Rhythmbox to restart the playback, the progress bar is frozen and there's no sound. It worked okay in 8.04 and previous versions of Ubuntu with this motherboard. I'm using HDA nVidia instead of your Intel chip, so it appears the problem isn't limited to your Gateway.

For me, quitting and restarting Rhythmbox fixes the problem. 

I tried following the Pulse Audio fixes in [this post]("http://ubuntuforums.org/showthread.php?t=789578&highlight=rhythmbox+resume"). It didn't solve the resume problem, but the quality of the sound is better. 

I tried suspending without pausing Rhythmbox and found that it knocked out my wired internet connection when I resumed and made no difference for playback. 

So far, no joy.

---

### Post by kaoskorruption on 2008-12-01
I've submitted a question at launchpad with no response in several days; here is some more information about the problem:

[https://answers.launchpad.net/ubuntu/+question/52793](https://answers.launchpad.net/ubuntu/+question/52793)

Here are some pictures of my sound settings:
[http://img91.imageshack.us/my.php?image=screenshotvolumecontrolcy9.png](http://img91.imageshack.us/my.php?image=screenshotvolumecontrolcy9.png)
[http://img84.imageshack.us/my.php?image=screenshotvolumecontrolph9.png](http://img84.imageshack.us/my.php?image=screenshotvolumecontrolph9.png)
[http://img118.imageshack.us/my.php?image=screenshotsoundpreferencn1.png](http://img118.imageshack.us/my.php?image=screenshotsoundpreferencn1.png)
[http://img118.imageshack.us/my.php?image=screenshotsoundpreferenhd9.png](http://img118.imageshack.us/my.php?image=screenshotsoundpreferenhd9.png)

[IMG]http://img91.imageshack.us/my.php?image=screenshotvolumecontrolcy9.png[/IMG]
[IMG]http://img84.imageshack.us/my.php?image=screenshotvolumecontrolph9.png[/IMG]
[IMG]http://img118.imageshack.us/my.php?image=screenshotsoundpreferencn1.png[/IMG]
[IMG]http://img118.imageshack.us/my.php?image=screenshotsoundpreferenhd9.png[/IMG]

So far nobody has helped. If you need more information, just ask and I will give you as much information as I can. I really appreciate any help!

---

