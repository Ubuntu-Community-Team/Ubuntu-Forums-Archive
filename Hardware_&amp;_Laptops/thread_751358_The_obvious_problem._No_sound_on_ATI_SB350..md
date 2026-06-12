---
title: "The obvious problem. No sound on ATI SB350."
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by rjsec4ever on 2008-04-10
I was viewing a post earlier, and forgot which one.

A user told me to do this.

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base-alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel
```

Sometimes, I get to the 3rd command, and a process is causing this module to run (I'm guess Ubuntu itself?) and I can not remove the module. Maybe there is some way to kill the  processes using the module? Anyway, the rest of the commands...

```
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base
|
> add *options snd-hda-intel probe_mask=8 model=auto* to end of file.
```

I did all that, and the sound worked after a reboot. But that was as root.
Reason: While using the most recent stable release of Kubuntu, I could ONLY boot in Recovery mode (due to GFX problems). When I signed on as root, the sound worked!!! But as myself, the user? No-go.

If you need computer specs...

Toshiba Satellite A105-S2051 w/ 2GB RAM
Intel Celeron M 1.7Ghz
ATI Radeon Xpress 200M 128MB
ATI SB350 a.k.a. Realtek HDA

Help please? Thanks!

---

