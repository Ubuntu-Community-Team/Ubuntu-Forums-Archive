---
title: "Why does sound not work on the newer Intel Bay Trail tablets?"
date: 2014-12-05
forum: Hardware
---

### Post by ronniepinsky on 2014-12-05
You probably know already that Dell Venue 8 Pro (original - 5000 series) and Asus T100 have working sound and are generally supported by Linux as seen here: [https://www.happyassassin.net/fedlet-a-fedora-remix-for-bay-trail-tablets/]("https://www.happyassassin.net/fedlet-a-fedora-remix-for-bay-trail-tablets/comment-page-2/#comment-458594")

What you may not know is that the current crop of Bay Trail devices all have non-working sound.  I would love for someone to prove me wrong on this point but I don't think it will happen.  I have tested these devices:
HP Stream 7
Toshiba Encore Mini 7
Toshiba Encore 2 8
Dell Venue 8 Pro 3000 series
Nextbook 8"

The result is the same.  They all have the same error:
```

baytrail-pcm-audio baytrail-pcm-audio: ipc: error DSP boot timeout


```

Further testing with the HP Stream 7 resulted in bypassing that error and creating an actual audio device with the firmware from this link: [https://chromium.googlesource.com/chromiumos/third_party/linux-firmware/+/refs/heads/stabilize-5339.B/intel/](https://chromium.googlesource.com/chromiumos/third_party/linux-firmware/+/refs/heads/stabilize-5339.B/intel/)

Unfortunately, sound playback still does not work even with playing with every alsamixer setting.

This means none of the current crop of Bay Trail devices today are usable.  Unless you help.  Thanks for your understanding.

---

### Post by ian-weisser on 2014-12-05
Seems like the Kernel gurus are already on the case (May 2013): See [https://groups.google.com/forum/#!topic/fa.linux.kernel/5domod_5Y6Y](https://groups.google.com/forum/#!topic/fa.linux.kernel/5domod_5Y6Y)
And your error message seems to indicate that the kernel recognizes the hardware.

Seems like Alsa is also already on the case (Feb 2014): See [http://mailman.alsa-project.org/pipermail/alsa-devel/2014-February/073132.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2014-February/073132.html) (and many more baytrail-specific threads later).

I would look for a newer release of Alsa. The current version of alsa-firmware-loaders in 15.04, 14.10, Jessie, and Sid is (pretty much) the same, 1.0.28-1, which was uploaded to Debian in 18 July 2014: See [https://tracker.debian.org/pkg/alsa-tools](https://tracker.debian.org/pkg/alsa-tools) . Lot of movement and bugfixes since then, so you might try to compiling a newer version directly from the upstream source. If you still have the problem, then please report the bug to Alsa.

I would also, as a good netizen, patrol the Ubuntu bug tracker and Debian bug tracker. Consolidate duplicate bug reports and upstream baytrail bugs that have not found their way to Alsa yet. Alsa may not know about the problem unless we -the users- tell them, and your experience and research can help many users improve their bug reports, highlight the correct problems for the Alsa developers, and get the bug (if any) fixed faster by preventing distractions.

Or, if you don't want to compile or triage bugs, then simply wait for Ubuntu 15.04. The support for this hardware seems on-the-way, though it has not landed yet.

---

