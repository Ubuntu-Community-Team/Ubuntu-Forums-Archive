---
title: "Help With Sound On Laptop"
date: 2010-02-14
forum: Hardware
---

### Post by izizzle on 2010-02-14
I am running Ubuntu 9.10 64 bit on a Gateway MT6460 laptop. Up till last night, the sound was working fine, and it was detected as stereo analog output. I updated the system last night and this morning the sound does not work, and it shows up as a dummy sound card. Any ideas?

---

### Post by IcarusR on 2010-02-14
This has been discussed on several threads recently.
There are several different solutions in this thread...

[http://ubuntuforums.org/showthread.php?t=1316634]("http://ubuntuforums.org/showthread.php?t=1316634")

Post 6 here talks about adding user to audio group... also other stuff if you have intel audio card.

[http://ubuntuforums.org/showthread.php?t=1384181]("http://ubuntuforums.org/showthread.php?t=1384181")

---

### Post by izizzle on 2010-02-14
I did what it said in the first link. I Removed alsa and pulseaudio and reinstalled. Before rebooting, I noticed that the sound was back on, and it detected it as Stereo Analog Sound. After the reboot, however, the sound was gone and it was back to Dummy output.

---

### Post by izizzle on 2010-02-14
I ran ```
sudo lshw -C sound
``` and got the following:

```
  *-multimedia            
       description: Audio device
       product: IXP SB4x0 High Definition Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:c0000000-c0003fff
```

---

