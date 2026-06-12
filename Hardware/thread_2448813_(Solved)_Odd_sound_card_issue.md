---
title: "(Solved) Odd sound card issue"
date: 2020-08-14
forum: Hardware
---

### Post by exploder on 2020-08-14
I installed Kubuntu on a newer HP dylxxx laptop and am having intermittent issues with pulseaudio recognizing the HDA Intel PCH onboard sound. Alsa shows the correct information and most of the time the sound works perfectly. Every so often when I boot the sound icon in the panel shows a no symbol on the speaker icon and sound will not work. Pulseaudio runs in the background unable to detect the sound card. The system hangs on restart and shut down when this occurs. If I do not kill the pulseaudio process the system has to be hard shut down, once rebooted sound works again. If I kill the pulseaudio process the system shuts down or reboots normal.

I have reinstalled pulseaudio. The system still might boot several times with no sound issue, then out of nowhere the problem returns. Here is the info related to sound.

```
description: Audio device
product: Smart Sound Technology Audio Controller
vendor: Intel Corporation
physical id: 1f.3
bus info: pci@0000:00:1f.3
version: 30
width: 64 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: driver=snd_hda_intel latency=32
resources: iomemory:400-3ff iomemory:400-3ff irq:148 memory:4000120000-4000123fff memory:4000000000-40000fffff

```

---

### Post by exploder on 2020-08-14
I might have a work around for the issue. I raised the priority of pulseaudio when there was no sound and the sound started working. I will use the laptop a day or so to see if the issue returns.

Edit: Problem returned....

Edit 2: Just noticed that when it happens system monitor shows "disk sleeping".

---

### Post by exploder on 2020-08-15
The more I dig into this problem the more I find. The issue is clearly with pulsaudio. Is there by chance a ppa with newer pulseaudio packages?

---

### Post by CelticWarrior on 2020-08-15
I would recommend updating UEFI ("BIOS") before anything else.

---

### Post by exploder on 2020-08-17
I installed Ubuntu and the 5.8.1 mainline kernel. Sound works perfectly now! I do get some kernel errors but likely the next Ubuntu point release will take care of that.

---

### Post by math492m on 2020-08-18
thanks this helped me to:-)

---

### Post by exploder on 2020-08-18
@ math492m

Your welcome! I was hoping this could be of use to others with similar problems.

---

