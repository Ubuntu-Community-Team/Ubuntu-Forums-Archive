---
title: "Pulseaudio emu10k1 trouble"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by diederick76 on 2009-04-26
I upgraded my laptop as well as my desktop box to Jaunty. My laptop gave no problems, but with my desktop box I can't figure out how to get the sound working properly. Rhythmbox, totem work fine now, Rosegarden, Audacity, Flash produce no sound at all.

I have an Audigy 1 sound card, which uses emu10k1 driver. ```
lsmod | grep emu10k1
``` revealed the dirver was loaded. ```
tail -f /var/log/messages
``` told me I didn't belong to the pulse-rt group, so I added myself to that group. That made at least Rhythmbox et al work, but on my laptop I apparently don't need to be.

When I type ```
pulseaudio
``` at a terminal, I get these:
```

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
W: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
W: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
E: module.c: Failed to open module "module-console-kit": file not found
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

```

Can someone tell me what I should do here? What is the pulse-rt group for? 

Thanks for any help,
Diederick

---

