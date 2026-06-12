---
title: "Alsa not working - help!"
date: 2008-09-15
forum: Hardware
---

### Post by simpsonsfreak on 2008-09-15
Hi everyone,
Here's my problem:
My sound was working fine until just now. When I try to run alsamixer from the terminal, it shows this:
alsamixer: function snd_ctl_open failed for default: No such file or directory

The output for sudo alsa force-reload is:
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/hayden/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/hayden/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

And the results of sudo lshw -C sound are:
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

I've tried a few things, but thus far none of them have worked. As I said, it was after I tried to do something as it was previously working.

Thanks to anyone who can help me in any way, I really appreciate it...

---

### Post by Casper Hansen on 2008-09-15
Can you use Pulse Audio?

---

### Post by nadalizadeh on 2008-09-15
list your current kernel modules by "lsmod" and see which one
is related to your sound card and "rmmod" it. then reload
with "modprobe"
Also close any applications that is probable to use sound feature.
rebooting might help too !

---

### Post by simpsonsfreak on 2008-09-15
> **Casper Hansen said:**
> Can you use Pulse Audio?

I'm not sure it works with my card as I've had (unrelated) problems before and alsa has been working until just recently.

---

### Post by simpsonsfreak on 2008-09-16
My problem has now been resolved thanks to iFvwm in the #ubuntu IRC channel - all I had to do was install the linux-ubuntu-modules package for my kernel!:popcorn:

---

### Post by Robbyx on 2008-11-03
> **simpsonsfreak said:**
> My problem has now been resolved thanks to iFvwm in the #ubuntu IRC channel - all I had to do was install the linux-ubuntu-modules package for my kernel!

How did you do that?
Can it be done through synaptic?

Robin

---

