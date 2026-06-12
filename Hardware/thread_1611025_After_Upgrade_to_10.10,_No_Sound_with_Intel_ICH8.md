---
title: "After Upgrade to 10.10, No Sound with Intel ICH8"
date: 2010-11-01
forum: Hardware
---

### Post by Githlar on 2010-11-01
Sound worked perfectly out of the box with Lucid, but after a web upgrade to Maverick, my sound devices (except for internal audio) suddenly and mysteriously disappeared. I've tried purging and re-installing all sound-related packages I can think of (alsa-base, pulseaudio, etc) but to no avail.

Relevant `lspci` output:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

`amixer info`:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

I've heard that installing some backport alsa modules from the ubuntu-audio-dev ppa, but there are no backport modules for the latest kernel.

Anybody have any ideas?

---

### Post by Githlar on 2010-11-01
It looks like the "Internal Audio" device listed in the sound properties is HDMI. I haven't tried it yet, but not even the PC speaker is listed :-k

---

### Post by Githlar on 2010-11-02
It turns out this was a problem that I've experienced only twice before. It was a hardware issue where the sound card was left in some kind of awkward state. All that was requird to fix it was power it down, unplug it and take out the battery for a few seconds.

---

### Post by holdfenytolvaj on 2010-11-06
Very strange, the same issue happened with me, and the same "solution" worked... Thanks sharing it!

---

