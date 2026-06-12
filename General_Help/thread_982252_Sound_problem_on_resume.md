---
title: "Sound problem on resume"
date: 2008-11-14
forum: General Help
---

### Post by zaomaster on 2008-11-14
I've got a ThinkPad T30 with this sound device

```
 *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

```

When I resume from suspend or hibernate the pitch the sound is shifted higher, like it was sampled at a higher rate than normal. Any ideas?

---

### Post by zaomaster on 2008-12-11
I figured it out.

PulseAudio was not unloading during suspend/hibernation, thus disallowing snd-intel8x0 from unloading. So when I resumed from suspend/hibernation there was some craziness going on when it tried to reload the module.

Solved!

Perfect install!

---

### Post by poit on 2009-03-11
> **zaomaster said:**
> I figured it out.

PulseAudio was not unloading during suspend/hibernation, thus disallowing snd-intel8x0 from unloading. So when I resumed from suspend/hibernation there was some craziness going on when it tried to reload the module.

Solved!

Perfect install!

Hi there.

Same problem here, could you be more specific about the fix?

Thanks

---

### Post by SyberKowboy on 2009-03-12
> **poit said:**
> hi there.

Same problem here, could you be more specific about the fix?

Thanks

+1

---

### Post by zaomaster on 2009-04-14
> **poit said:**
> Hi there.

Same problem here, could you be more specific about the fix?

Thanks

Sure, sorry it took so long to reply.

For some reason the gnome volume panel control is keeping the sound module from unloading during suspend/hibernation. So I just removed it and everything works great now. I use the dedicated buttons on my laptop to control volume.

---

### Post by poit on 2009-04-27
> **zaomaster said:**
> Sure, sorry it took so long to reply.

For some reason the gnome volume panel control is keeping the sound module from unloading during suspend/hibernation. So I just removed it and everything works great now. I use the dedicated buttons on my laptop to control volume.

This didn't fix the problem either, but this did. I found this Pulseaudio guide at:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

I followed all the steps in section A. (I'm running Jaunty now). I suspect installing the libraries in part A-2 did it, but it could have also been deleting the old config files in part A-1. (part A-3 didn't apply, I didn't have the libflashsupport installed anyway. 
I've been fighting this for about 6 months now. Hurray!

---

### Post by poit on 2009-05-04
OK, STILL not fixed, but more info....and I'm over my head on this one.

The chipmunk audio goes back to normal if I delete the following file:

~/.pulse./somesortofhashcode/native

This native file is of size 0 and is listed as an inode socket. So, what is this, why does deleting it return the sound pitch to normal (until a reboot, which restores the file), and does this give anyone a clue to a permanent fix?

---

