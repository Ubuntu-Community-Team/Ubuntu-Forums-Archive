---
title: "Random Sound Issues (works then doesnt?!)"
date: 2008-07-01
forum: Hardware
---

### Post by grimdeath on 2008-07-01
My system is in my signature, the sound problems are really weird, ive been running Hardy since Friday with little to no sound problems once I figured out a working configuration but for some reason now some sounds are not working. The only change tonight was installing Quake Wars demo and compiz-switch to keep the game from bugging out if compiz is on.

What works:
-system sounds, login, etc..
-streaming videos online, mixed formats
-mp3 and ogg files store locally

What doesnt work/messes up:
-I had sound working ONE time after I installed and restarted in the Quake Wars demo but now it wont work after multiple restarts
-Streaming videos, they work 9/10 times but tonight they quit working after Quake did.

This is all while system sounds and local music files STILL WORK! I can listen to music right now but I cannot watch a streaming video, no sound on those...wtf!? Any ideas?

I have my system > prefs > sounds set to:
autodetect
autodetect
autodetect
Alsa
Device: Audigy 2 ZS SB0350 (alsa mixer)

And I have my volume control set to: File > Change Device > Audigy 2 ZS SB0350 (alsa mixer)

Let me know if you have any ideas what I can do to resolve this!

*edit*
after a bit of tinkering myself I got it working for streaming vids, I right-clicked my sound icon next to the clock and went to preferences for that and changed the Volume Control Prefs to my sound card option. I also selected PC Speakers in the list below devices in the system > prefs > sounds. Just tested in Quake and sounds working there again...hope this is a permanent fix but let me know if this is a known issue. Thanks!

---

### Post by blueturtl on 2008-07-01
Certainly a known issue: the sound in Hardy default installs is broken!

You need to follow this guide to fix latency and stuttering+issues with multiple programs using sound simultaneously:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by grimdeath on 2008-07-01
my sound's been working fine since last night, streaming vids, music, games all working fine. thanks for the heads up at that thread though.

---

