---
title: "Need to restart alsa to hear sound every reboot"
date: 2010-02-27
forum: Hardware
---

### Post by corwinspyre on 2010-02-27
I upgraded yesterday to 9.10 and am having a strange trouble with sound on my HP tx2500 laptop.  

When I installed from CD, it was working fine, but after 'apt-get upgrade'ing, it stopped working.  I checked the volume control, and there was nothing in "Input", "Output", or "Hardware".

There is a problem with the HP tx* series of laptops that requires a tweak to alsa-base.conf, so I tried that and afterwards ran "sudo /etc/init.d/alsa-utils stop", "sudo alsa force-reload", and finally "sudo /etc/init.d/alsa-utils start", causing it to work.

However, after the next reboot, there again was no sound.  At a loss, I checked alsa-base.conf to see if my change was still there, and it was.  I ran the three alsa commands again, and it started working again.  

The same thing happens each reboot.

Anyone know why it would do this or how to fix it?

---

### Post by bliffle on 2010-02-27
I was hopeful, so I tried that on my no-audio Thinkpad X60s (audio works on XP partition), but no joy.

Here's what I got:
```

john@JHX60s:~$ sudo /etc/init.d/alsa-utils stop
[sudo] password for john: 
 * Shutting down ALSA...                                                 [ OK ] 
john@JHX60s:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
Terminating processes: 2001lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
 2745lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
 2759lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
 2773lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 2787lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 2801(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 2801(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
john@JHX60s:~$ sudo /etc/init.d/alsa-utils start
 * Setting up ALSA...                                                    [ OK ] 
john@JHX60s:~$ 

```

The little silver audio buttons above the KB don't do anything either, and there's no onscreen display of audio level.

---

### Post by corwinspyre on 2010-02-27
> **bliffle said:**
> I was hopeful, so I tried that on my no-audio Thinkpad X60s (audio works on XP partition), but no joy.

Here's what I got:
```

john@JHX60s:~$ sudo /etc/init.d/alsa-utils stop
[sudo] password for john: 
 * Shutting down ALSA...                                                 [ OK ] 
john@JHX60s:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
Terminating processes: 2001lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
 2745lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
 2759lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
 2773lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 2787lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 2801(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 2801(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
john@JHX60s:~$ sudo /etc/init.d/alsa-utils start
 * Setting up ALSA...                                                    [ OK ] 
john@JHX60s:~$ 

```

The little silver audio buttons above the KB don't do anything either, and there's no onscreen display of audio level.

I get a similar 'error', so there's no problem there.  I don't think you have the same problem as me, but I can show you how to find the fix I made first to get my sound working.

Hit Alt-F2 and type in "gksu gedit /etc/modprobe.d/alsa-base.conf".  It'll ask for your password then bring up a text document.  Scroll to the bottom, and in a new line type "options snd-hda-intel model=thinkpad".  Hit ctrl-s (to save), and then either reboot or run the three commands I have above.  See if that works.

---

### Post by bliffle on 2010-02-28
Did that, no change.

Now I wonder if I should back out the change to 'alsa-base.conf'?

---

### Post by corwinspyre on 2010-02-28
I think you'll need to keep that in alsa-base.conf whenever we figure out what's actually wrong.  I got it from here: [http://ubuntuforums.org/showthread.php?p=6573913#poststop](http://ubuntuforums.org/showthread.php?p=6573913#poststop) (ctrl-f and type in t60; you'll see people with your model need to do that for everything to work right).

Since you don't even get the on screen audio level, I'm wondering if your card is showing up at all.  Can you please type in "sudo lshw -c Multimedia" and post what comes out?  

Also, did you recently install Ubuntu, or how long has it been installed?  And, what version are you on?

---

### Post by bliffle on 2010-03-01
I installed 9.10 fresh on this X60s about 4 months ago and it worked fine until about a month ago.

Here's the "sudo lshw -c Multimedia' display:

```

john@JHX60s:~$ sudo lshw -c Multimedia
[sudo] password for john: 
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:17 memory:ee240000-ee243fff
john@JHX60s:~$ 

```

---

