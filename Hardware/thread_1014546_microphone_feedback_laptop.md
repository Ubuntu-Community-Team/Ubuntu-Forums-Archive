---
title: "microphone feedback laptop"
date: 2008-12-17
forum: Hardware
---

### Post by kacheng on 2008-12-17
Has anyone encountered crazy microphone feedback from their laptop?

My laptop (IBM T42 running 32-bit Ubuntu Intrepid) occassionally starts emitting a high pitched whine.

I finally traced it to microphone/speaker feedback, and have turned down the volume settings for the microphone, which seems to reduce it for now.

[I did find one Launchpad bug for Hardy, indicating it was a kernel problem that was fixed for Intrepid, but obviously this isn't the case for me.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209040]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209040")]

Anyone else seen this?  Any tips on how I fix/troubleshoot it?

---

### Post by dagoth_pie on 2008-12-18
Sounds a pain to get running perfect, try switching between alsa and oss, installing other alsa/oss packages, oh but first, you may want to double click the volume control, select the switches tab, and make sure mic boost isn't ticked, if you mic is too sensitive already i guess it could do that

---

