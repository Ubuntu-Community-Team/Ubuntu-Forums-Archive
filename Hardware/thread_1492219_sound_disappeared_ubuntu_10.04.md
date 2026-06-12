---
title: "sound disappeared ubuntu 10.04"
date: 2010-05-24
forum: Hardware
---

### Post by amohell on 2010-05-24
I have a problem with my sound card Creative audigy se 7.1 (PCI).  One month ago I've installed Ubuntu 10.04, everything works fine including the sound card. This morning I started the computer, sound doesn't work anymore (no system sounds, VLC, youtube). When I boot to Windows Xp the sound card works fine, so I don't think the hardware is damaged. The sound card is still recognize as &#8220;CA0106 soundblaster&#8221;. When I boot the system you can hear the static energy disappear. Does anybody have a solution?
 

I understand I have to post log files etc. but I have no idea wich log files.

---

### Post by amohell on 2010-06-01
I still have the same problem, the boot errors disappeared. But no sound at all, does anybody have a suggestion? I think it's sad because Ubuntu works very well, but with no sound I get back to Opensuse (I think the support forum of Opensuse a lot more responsive :oops:).

---

### Post by amohell on 2010-10-26
After using Opensuse for a while I thought I want Ubuntu back, it's two times faster. But two days later, after a fresh install of Ubuntu 10.04  sound stopped working again! In MS xp and Opensuse it work just fine. Is there nobody out there with a solution?

> Oct 24 15:54:11 tim-MS-7100 pulseaudio[1559]: pid.c: Daemon already running.
Oct 24 16:53:24 tim-MS-7100 python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Oct 24 17:06:48 tim-MS-7100 pulseaudio[1454]: pid.c: Daemon already running.
Oct 24 23:41:12 tim-MS-7100 pulseaudio[1406]: protocol-native.c: Failed to push data into queue
Oct 24 23:42:01 tim-MS-7100 pulseaudio[1406]: last message repeated 2 times
Oct 25 00:29:06 tim-MS-7100 pulseaudio[1427]: pid.c: Daemon already running.
Oct 25 00:52:11 tim-MS-7100 pulseaudio[1388]: protocol-native.c: Failed to push data into queue
Oct 25 00:52:56 tim-MS-7100 pulseaudio[1388]: last message repeated 3 times
Oct 25 01:03:11 tim-MS-7100 pulseaudio[1388]: ratelimit.c: 34 events suppressed
Oct 25 01:03:45 tim-MS-7100 pulseaudio[1388]: ratelimit.c: 138 events suppressed
Oct 26 01:11:10 tim-MS-7100 pulseaudio[1438]: pid.c: Daemon already running.
Oct 26 17:57:11 tim-MS-7100 pulseaudio[1458]: pid.c: Daemon already running.
Oct 26 21:20:54 tim-MS-7100 pulseaudio[1459]: pid.c: Daemon already running.
Oct 26 21:21:19 tim-MS-7100 pulseaudio[1774]: pid.c: Daemon already running.


---

### Post by amohell on 2010-10-26
After using Opensuse for a while I thought I want Ubuntu back, it's two times faster. But two days later, after a fresh install of Ubuntu 10.04  sound stopped working again! In MS xp and Opensuse it work just fine. Is there nobody out there with a solution?

> Oct 24 15:54:11 tim-MS-7100 pulseaudio[1559]: pid.c: Daemon already running.
Oct 24 16:53:24 tim-MS-7100 python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Oct 24 17:06:48 tim-MS-7100 pulseaudio[1454]: pid.c: Daemon already running.
Oct 24 23:41:12 tim-MS-7100 pulseaudio[1406]: protocol-native.c: Failed to push data into queue
Oct 24 23:42:01 tim-MS-7100 pulseaudio[1406]: last message repeated 2 times
Oct 25 00:29:06 tim-MS-7100 pulseaudio[1427]: pid.c: Daemon already running.
Oct 25 00:52:11 tim-MS-7100 pulseaudio[1388]: protocol-native.c: Failed to push data into queue
Oct 25 00:52:56 tim-MS-7100 pulseaudio[1388]: last message repeated 3 times
Oct 25 01:03:11 tim-MS-7100 pulseaudio[1388]: ratelimit.c: 34 events suppressed
Oct 25 01:03:45 tim-MS-7100 pulseaudio[1388]: ratelimit.c: 138 events suppressed
Oct 26 01:11:10 tim-MS-7100 pulseaudio[1438]: pid.c: Daemon already running.
Oct 26 17:57:11 tim-MS-7100 pulseaudio[1458]: pid.c: Daemon already running.
Oct 26 21:20:54 tim-MS-7100 pulseaudio[1459]: pid.c: Daemon already running.
Oct 26 21:21:19 tim-MS-7100 pulseaudio[1774]: pid.c: Daemon already running.
When I reload the alsa moduele:
> killall pulseaudio
sudo alsa force-reload I get this:
> lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim2/.gvfs
      Output information may be incomplete.
Terminating processes: 2442 2449lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim2/.gvfs
      Output information may be incomplete.
 2483lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim2/.gvfs
      Output information may be incomplete.
 2498lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim2/.gvfs
      Output information may be incomplete.
 2513lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim2/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 2528lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim2/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 2542(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tim2/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 2542(pulseaudio). 
Unloading ALSA sound driver modules: snd-ca0106 snd-ac97-codec snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-ca0106 snd-ac97-codec snd-pcm snd-rawmidi snd-timer snd-seq-device snd-page-alloc).
Loading ALSA sound driver modules: snd-ca0106 snd-ac97-codec snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc

---

### Post by sisyphist on 2010-11-21
Have you had any luck finding a solution? The exact same thing just happened to me! And I can't think of any cause for it.

To be specific: I am using 10.04; after years of working, sound disappeared; only "Dummy output" shows in sound preferences; I get the same set of errors when I follow the alsa directions above.

Sigh...I am really trying to keep up the love, but ubuntu keeps breaking things that should just work!

---

### Post by sisyphist on 2010-11-21
Fixed it with these steps:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils

After verifying ubuntu could see my card with:
aplay -l

As (very helpfully!) described at:
[http://ubuntuforums.org/showthread.php?t=205449]("Comprehensive Sound Problems Solution Guide")

---

### Post by amohell on 2010-11-22
> **sisyphist said:**
> Fixed it with these steps:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils

After verifying ubuntu could see my card with:
aplay -l

As (very helpfully!) described at:
[http://ubuntuforums.org/showthread.php?t=205449]("http://Comprehensive%20Sound%20Problems%20Solution%20Guide")

thank you, this solved my problem. Although I needed to remove pulseaudio instead of ALSA

---

### Post by sisyphist on 2010-11-22
Gack! I spoke too soon - when I booted up this morning, the problem had returned! I can't follow those steps every time. I'll keep looking, but I'd appreciate knowing if the same thing happens to you.

---

### Post by sberla54 on 2010-11-22
I think i have a similar problem, i you wanna take a look: [http://ubuntuforums.org/showthread.php?p=10146018](http://ubuntuforums.org/showthread.php?p=10146018)

I'm still not being able to fix it...

I haven't already tried to reinstall alsa because i'm at work...i'll try as soon as i come back to home....by the way, i've tried a lot of other procedures, if you wanna try them too...

UPDATE:
I've removed and reinstalled alsa, with:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

```and then
```

sudo apt-get install ubuntu-desktop

```that was deleted too, but nothing changed. The problem is still here.

I think my problem is a little bit different...my audio card is correctly detected, seems to work but i can't hear a sound....

@ [sisyphist]("http://ubuntuforums.org/member.php?u=1192074") 
I suggest you to take a look at my post and, maybe, join it. 
You should try the Alsa Update Script and you could post some of the outputs i've posted, so we can bettere analize the problem...
I suggest you to try Ubuntu 10.10 live, too, and if everything works, save the outputs of the commands i've quoted on my post, so you can try to clone the same settings on the installed 10.04...

---

