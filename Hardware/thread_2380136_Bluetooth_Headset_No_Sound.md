---
title: "Bluetooth Headset No Sound"
date: 2017-12-13
forum: Hardware
---

### Post by ulkeshkosh on 2017-12-13
I have been struggling with Bluetooth headsets in Linux for quite some time. Things just never work quite right. And even when they seem like they might, they stop working after some time.

I have captured an OBS video of my current issue which is one that has seemingly plagued me across multiple Bluetooth headsets:
[https://www.youtube.com/watch?v=xwUU7ZoTEGc](https://www.youtube.com/watch?v=xwUU7ZoTEGc)

My setup: [https://imgur.com/hKrLzWR](https://imgur.com/hKrLzWR)
Kernel: 4.13.0-19-generic
My system is up to date

Issues:

[LIST=1]
[*]When a Bluetooth headset is paired, and then turned off, after turning back on, it will not immediately connect. I have no choice but to go to the Bluetooth Settings and attempt to connect manually, which leads to the next issue...
[*](Shown in video) When attempting to manually connect in the Bluetooth settings, I have to click the slider multiple times before it even attempts to connect (This has occurred on multiple Ubuntu versions and Arch Linux for me). On some Bluetooth headsets it simply won't connect (even though those headsets had already been paired) requiring me to un-pair and re-pair (often times this occurs after a reboot).
[*](Shown in video, per se) Now, I had paired and connected the specific headset in the video above (Apple AirPods) even with the above issues, but sound would still come out fine once I got past those issues. As of two days ago, sound will no longer come out. When paired/connected to any other device (Apple and non-Apple alike), the headset works perfectly fine.

[/LIST]
Things I have tried:

[LIST=1]
[*]Reinstalled pulseaudio-module-bluetooth
[*]Tried a2dp.py script from [https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae](https://gist.github.com/pylover/d68be364adac5f946887b85e6ed6e7ae)
[*]Tried removing/re-pairing/re-connecting
[/LIST]

Almost every blog and podcast will now say that Bluetooth audio just works, but that is not my experience.

Thanks for any and all help given!

---

### Post by curcanstefan on 2018-04-24
Hi,
I see you got no answers. Did you get your problem fixed? I happen to have the same bluetooth device but different problem. Maximum volume is never good enough. It is always below my normal listening preference. Did you also encounter this, or only the no sound issue?
As a reference I opened a thread too: [https://bbs.archlinux.org/viewtopic.php?pid=1779791](https://bbs.archlinux.org/viewtopic.php?pid=1779791)

---

