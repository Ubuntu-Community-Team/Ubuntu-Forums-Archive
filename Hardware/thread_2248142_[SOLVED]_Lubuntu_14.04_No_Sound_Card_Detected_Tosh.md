---
title: "[SOLVED] Lubuntu 14.04 No Sound Card Detected Toshiba Satellite A105 S2712"
date: 2014-10-12
forum: Hardware
---

### Post by MaxWeber on 2014-10-12
-------------------------------------------------------
Solution: USB booted Vista 32bit... good to go
-------------------------------------------------------[URL="http://www.alsa-project.org/db/?f=2e2628d0062ff59a8077eb0b04035ca29760eadd"]

http://www.alsa-project.org/db/?f=2e2628d0062ff59a8077eb0b04035ca29760eadd[/URL]

I'm a newcomer to lubuntu and everything has run smoothly except this pesky sound issue. I haven't been able to get any sound after using the troubleshooting guide, searching through various forum posts, installing and removing various things, changing settings. Nothing seems to be working. Most of the threads I find related to my hardware configuration never reach a solution. Am I trying to run ubuntu on an incompatible laptop?


max@Max-Computer:~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fabf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

--------------------------------------
It seems to be detected on some part of the system, but not detecting in alsa.


Thank You,
-Max

---

### Post by Yellow Pasque on 2014-10-12
```
[   12.000908] snd_hda_intel 0000:00:1b.0: Codec #0 probe error; disabling it...
[   12.044076] snd_hda_intel 0000:00:1b.0: no codecs initialized
```
Codec probe errors are rough. I see you've already tried playing with the probe mask option. The only other things I suggest are disabling the audio codec in the BIOS and then reenabling it on a later boot. Other long shots would be updating the BIOS (if you're running an old one) and/or doing a hard reset on the laptop (if Toshiba has such a thing similar to HP).

---

### Post by MaxWeber on 2014-10-12
I have the BIOS updated. There is no way to change audio settings in the BIOS on this laptop unfortunately. Its very watered down. I heard somewhere that since the audio chipset isn't plug and play it would be tricky to get it working. What's frustrating is that when searching this forum, I found other users who reported this model laptop as working with no issues! I might need to install an older version of ubuntu I suppose. I heard that many people lose functionality when upgrading.

---

### Post by MaxWeber on 2014-10-13
Update: I installed 12.10 and it works... but 12.10 isn't supported so I have to figure out what to do next.

Lubuntu 12.10 works, Ubuntu 12.04LTS doesnt work.

I've seen some people running 14.04 on an older kernel which might be a solution

---

