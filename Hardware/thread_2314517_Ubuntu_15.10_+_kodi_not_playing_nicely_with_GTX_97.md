---
title: "Ubuntu 15.10 + kodi not playing nicely with GTX 970"
date: 2016-02-21
forum: Hardware
---

### Post by timfenney on 2016-02-21
Hey all,

Looking for some help here with wiley wonderbeast 15.10, kodi, and my poor 970.

I have tried all of these:

1 - install 15.10 amd64 desktop
   - additional drivers -> switch from nouveau to nvidia proprietary

2 - install 15.10 amd64 desktop
   - install "graphics drivers ppa"
   - install nvidia-355

3 - install 15.10 amd64 desktop
   - install "graphics drivers ppa"
   - install nvidia-361

4 - install 15.10 amd64 desktop

I then install kodi from the team-xbmc ppa, and log in to the kodi session (there are 2, but usually the first one) from lightdm, and enable airplay, etc.

When I use the Android app as a remote (official kodi one or yatse) it appears to work fine (I don't have content sources set up so no play back was tested). However when I attempt to airplay a video, yatse can wake up kodi, the fans spin up, but nothing is played. When I try to share a photo from Android (through yatse, again), my kodi screen goes black.

From kodi I have also tried (with all of the above ubuntu/nvidia driver combinations) to disable all hardware video decoding options from Settings -> Advanced -> Video Settings -> Acceleration (and "auto" changed to "software").

Does this sound like a video driver problem? Does anyone have the magic incantation to make this setup work?

---

### Post by timfenney on 2016-02-22
Well, crap.

I wasted a lot of time, because I had assumed it was a driver problem. I didn't test anything.

So I figured I'd work out what was borked, one thing at a time.

First up, the nvidia drivers. 15.10 + nvidia-361 is working flawlessly. It was such a relief to see watch the unigine heaven benchy in phoronix test suite.

Second, kodi. I installed the TED video plugin, and video playback was butter smooth.

Third, my Android file manager. In Android, you can typically tap on a file in a file manager, and it will allow you to pick from a list of programs & actions with which to open that file. For videos, Yatse's "play to media center" was the option I was using.

So I switched from the default Asus file manager to ES File Explorer, and still got the same problem as initially described.

Finally, Yatse itself. I had installed the app, but there was a second, for-pay component I had installed today, and I had not yet rebooted the phone since then. I rebooted, and tried again.

Video Airplay from Android is now working perfectly.

---

