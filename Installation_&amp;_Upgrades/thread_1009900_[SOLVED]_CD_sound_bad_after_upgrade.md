---
title: "[SOLVED] CD sound bad after upgrade"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by vikigal on 2008-12-13
I have been using 7.10 since last spring. I bought a new IBM loaded w/Ubuntu only and have loved it. However, last week I finally gave in and upgraded to 8.04. Almost everything is fine except my cdrom drive. It keeps telling me it is unable to mount volume. I have looked through the bug reports but can´t seem to find anything that particularly helps me.

I cannot play any CDs at all, data or music. At first it would not recognize any cd at all. After reading, reading, and more reading, I have tried several fixes, using the greatly feared terminal. I copied and pasted several commands that I have found here so that now a music cd shows up and is read but the sound is really, really bad. It sounds skittery, like it is skipping, like vinyl did when scratched. Data cds, with pictures or text, are not read at all.

I can play downloaded music, my mp3 player works, no problems with music/videos online using firefox.

I feel like this is probably a simple thing, but playing around is making me nervous especially since I am also having a problem installing the scan portion of my hp 4480 printer. But that is for another post, another day...Could there be a missing media packet?

HELP! Thanks for reading this long-winded thing. I am willing and able to post whatever you need to know to fix this.

---

### Post by vikigal on 2008-12-23
I solved this issue by disabling pulseaudio and re-installing the driver for my soundcard. Just using alsamixer now. After posting this I went on to totally destroy my sound and my cd-drive. I totally lost sound and contact with the cd drive. Since I disabled pulseaudio in the System > Preferences>Sessions area, and any other place short of un-installing, things are back to normal, almost. The only thing I need to do is change some permissions that I messed up with tinkering.

---

