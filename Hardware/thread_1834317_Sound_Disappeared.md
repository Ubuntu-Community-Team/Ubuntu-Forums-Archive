---
title: "Sound Disappeared??"
date: 2011-08-27
forum: Hardware
---

### Post by ingarion on 2011-08-27
This problem most likely surfaced after I uninstalled KDE from my laptop (HP Mini 210 - Ubuntu 11.04). It's possible that it also uninstalled some dependencies that ALSA, Pulse, etc. needed. Or the problem could have come from a couple of software updates. Either way, I can't seem to get sound back onto my computer. 

The volume control icon is missing from my top panel. There is a small, blank space where it used to be, and it is clickable, but there is no icon. When I do click on it, that space is embedded, or "sinks in," to the panel as all the other icons do, and I can see the edge of a drop-down menu appear (maybe 2-3 pixels wide). My keyboard also has manual volume controls, but pressing them does nothing. Normally, my mute button is only lit orange when I have mute enabled, and now the light is always orange, and I cannot change it. System > Preferences > Sound also does nothing; my bottom panel opens up a window that says "Starting Sound" but nothing pops up. 

Here is the audio section from "lspci -v | less"
```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 3594
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at 94200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```I also don't know how important this is, but this is what I get from running "wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh": [URL="http://www.alsa-project.org/db/?f=d45f3068462f9aa0bf219ebb8e800773bc6b7fd5"]http://www.alsa-project.org/db/?f=d45f3068462f9aa0bf219ebb8e800773bc6b7fd5
[/URL] 
Any help is greatly appreciated. :D

---

