---
title: "Audio is distorted and slow"
date: 2016-09-07
forum: Hardware
---

### Post by duduamar on 2016-09-07
Hi

I have Ubuntu 16.04.1 running on Intel NUC i5 connected through HDMI to LG TV (UF7300 if the exact model is important).
Sometimes the audio is distorted and slow, and restarting the NUC solves it until next time.

Has anyone encountered this as well?

Thanks.

---

### Post by i-jeff-h on 2016-11-04
I too am having this same problem, of slow audio when playing YouTube videos or other audio, from within Firefox (and Chrome too?).
I also have the Intel NUC i5, and I also think that rebooting does temporarily fix the problem.
I have searched the net for any information regarding this issue, and find nothing... but wait...

Actually, I just now found this (which appears to be applicable):
    [https://01.org/linuxgraphics/forum/graphics-installer-discussions/video/audio-slow-mo-after-update-ubuntu-15.10](https://01.org/linuxgraphics/forum/graphics-installer-discussions/video/audio-slow-mo-after-update-ubuntu-15.10)
  
which, ultimately points to this fix:
    [URL="https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS"]https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS
[/URL]
Update: the above fix does remedy the slow audio problem (as I can now play Youtube videos with no sound issues).

---

