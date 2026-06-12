---
title: "[SOLVED] [SOLVED] vaio external speakers from docking station problem"
date: 2008-11-02
forum: Hardware
---

### Post by metalgtr on 2008-11-02
In an [archived post]("http://ubuntuforums.org/showthread.php?t=740579"), I sought help with my Sony Vaio VGN-A290, which would stop producing sound when attached to the docking station (but sound was OK when it was undocked). Now that I've upgraded to Intrepid, all it took was un-muting IEC958 in alsamixer to make sound OK. FYI, all of the settings for my Alsa are the following now:

Master - 57
Master Mono - 81
Headphone - 71
3D control - MM (Switch Off)
PCM - 81
PCM Out - pre 3D
Line - MM
CD - 81
Mic - MM
Mic Boost - MM
Mic Select - Mic1
Phone MM
IEC958 - 00 (<-- this was the one that did it)
IEC958 Playback AC97-SPSA - 0 (note turning this up stopped the sound)
PC speaker - MM
Aux - MM
External Amplifier - 00

Thanks - Hope this helps someone else!

---

