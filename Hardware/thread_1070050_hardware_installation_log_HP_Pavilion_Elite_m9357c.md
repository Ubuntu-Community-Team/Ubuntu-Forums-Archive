---
title: "hardware installation log: HP Pavilion Elite m9357c desktop"
date: 2009-02-14
forum: Hardware
---

### Post by sixsmith on 2009-02-14
I have installed Ubuntu 8.10 Intrepid Ibex on my HP Pavilion Elite m9357c. I have opened this thread to store solutions to problems as they arise, so that other users of this machine can easily locate solutions.
Install notes so far:
1) am using HDMI connection to monitor. Computer came with DVI-to-VGA adapter, but worked badly-- streaky,shaky etc. My guess is a bad adapter ($5 plastic part), but luckily I had an HDMI cable, works fine.
2) On third boot, system fan failed. HP technician walked me through re-seating fan connections, which worked.
On to the hardware:
1) video. Ubuntu prompted me to install the nonfree NVIDIA drivers, which I did. Everything works OK, including full resolution. Haven't tried any games, can't report on 3D etc.
2) sound playback. Rhythmbox directed me to all the nonfree drivers needed to make sound work. ISSUE: sound is quite quiet, with computer piped to stereo, volume at '20' is equivalent to CD on stereo at '10'. However, with computer cranked, stereo volume can be cranked also, without apparent distortion.
3) wireless. wifi adapter on this machine is rt2860, which reports as 'ralink 0781' in lspci. Ralink driver has been built into a .deb package, easy to download and install: [http://packages.debian.org/sid/all/rt2860-source/download](http://packages.debian.org/sid/all/rt2860-source/download)

Still to report on: will update post:
MythTV (machine has a PCI express TV tuner)
sound input

---

