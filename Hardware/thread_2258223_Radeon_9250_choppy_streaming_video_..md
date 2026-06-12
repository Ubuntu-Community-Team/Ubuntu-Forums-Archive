---
title: "Radeon 9250 choppy streaming video ."
date: 2014-12-25
forum: Hardware
---

### Post by pjones2 on 2014-12-25
So I've recently installed 12.04.05. My main goal for this is to be a media machine. Streaming video, music, DVDs. Things like that. I have a Radeon 9250 with S video output to my television. When I am watching a DVD or a video that is on the computer. The run perfectly fine with no issues. When I move to streaming video (Netflix, Crackle, TubiTV) my video becomes choppy. Audio playback is spot on perfect. But the video is too choppy. It seems to drop frames, almost like watching claymation.
Any ideas of what could be causing this?
I'm lost, I've tried updates, drivers. I don't know.

Thank you in advance.

---

### Post by QIII on 2014-12-25
Hello!

The Radeon 9250 is an older card that AMD/ATI no longer supports with a driver that will work for any version of Ubuntu beyond 12.04.1 due to the version of X Server used.  Most other distros use versions of X Server that are also too new.

You will have to stick with the default open source Radeon driver supplied with Ubuntu at installation, so if you have attempted to install a proprietary driver you should attempt to uninstall it.

With a card that old, you may not be able to overcome the performance shortcomings.  Are you attempting to view Netflix content in Firefox, Chrome, other?

---

### Post by Yellow Pasque on 2014-12-26
I'm guessing it takes more CPU to stream the video. The video card probably doesn't have much to do with it.

> The Radeon 9250 is an older card that AMD/ATI no longer supports with a driver that will work for any version of Ubuntu beyond 12.04.1
The last proprietary driver AMD released for this card was in 2006. Ubuntu 12.04.1 would not even allow one to use that ancient driver.

---

