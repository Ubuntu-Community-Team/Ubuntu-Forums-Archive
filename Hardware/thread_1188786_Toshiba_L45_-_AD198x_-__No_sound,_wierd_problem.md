---
title: "Toshiba L45 - AD198x -  No sound, wierd problem?"
date: 2009-06-16
forum: Hardware
---

### Post by AoSteve on 2009-06-16
I have NO luck with hardware..  It's funny though, my 2000 built XP 1700+ works full out with 9.04 and I didn't have a single hitch..

Anyways, I can't get sound on this thing for the life of me..  I'll let the output do the talking..   I've tried every guide, but I think I've found the problem isn't in the model itself, but something different...

lspci -v
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at ff63c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```Ok, so that looks right..  now...  

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Well, we've figured out it's the AD198x...   I tried EVERY possible change on that .conf file possible...  Nothing changes the following two outputs.   One of the guides I found shows how to kill the pulseaudio and reload alsa..  You'll see the entire set of commands as I ran them, and this doesn't matter which model I change to in the .conf file..

```

steve@Toshiba:~$ killall pulseaudio
steve@Toshiba:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/steve/.gvfs
      Output information may be incomplete.
Terminating processes: 5983lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/steve/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/steve/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/steve/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
steve@Toshiba:~$ pulseaudio -D
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: main.c: Daemon startup failed.
steve@Toshiba:~$ 

```The "Daemon startup failed." is bolded in red and I think this is one of many problems creating my sound problem...   The sound worked flawlessly under Vista Home Premium, and it was registered as a Realtek audio device.   I haven't even had a BLIP of sound come from this machine, and I don't know where to go with it now..   Any idea's?  

Like I said though, I think I've tried every single idea on guides, solved posts, and other things aside from upgrading my alsa.  Maybe this is the answer, maybe not.  I just need some ideas.  

Thanks ahead of time,
Steve

---

### Post by AoSteve on 2009-06-16
Bump?   anyone?  LoL

---

### Post by AoSteve on 2009-06-17
I tested the 9.04 Live CD, and playing around in the terminal with alsa and pulseaudio, the SAME thing..   I have no idea..  I have no luck with sound hardware.

---

### Post by AoSteve on 2009-06-24
I've got sound!!!!!!!!!!!!

Woohoo,  after a lot of time spent trying to get it work I did the following through guides along the forums here.

I installed the updated alsa to no avial and uninstalled it as well.  I reinstalled the alsa from the 9.04 Live CD and got it back to normal.  Still no sound.

I worked with every possible solution in Pulseaudio...  Nothing...

I was talking to a great friend, DemonBob and he told me of a file that I've tried before..   

```

sudo gedit  /etc/modprobe.d/alsa-base.conf

```

I attempted resetting the snd-hda-intel from auto to 3stack as I've tried before.  I didn't think it'd work as I've tried just about every option like that before hand...

Well I rebooted and no drums...   I looked at my volume control and hit the mute button, which was checked, and boom  SOUND..

I'm not sure what enabled it, but adding the 3stack option this time worked.   I'm thinking it had something to do with uninstalling the new alsa and reinstalling from the CD.   That took a bit of work, had to do a LOT of research here on the forums about uninstalling from the command line but I finally got it back to original without reinstalling ubuntu completely.

So, now I have sound, not exactly what made it work correctly, but it works now.   It's a GREAT feeling to have sound on the go! :)

---

### Post by AoSteve on 2010-01-09
Just for future reference for myself and others here at UF.org...   The actual fix is as follow.   I simply changed the following lines in the file.

```
options snd-hda-intel power_save=10 power_save_controller=N
```

Was switched to :

```
options snd-hda-intel probe_mask=1 model=3stack
#options snd-hda-intel power_save=10 power_save_controller=N
```

This enabled the sound perfecly for me.   :)

---

