---
title: "Plugging in headphones doesn't mute speakers"
date: 2012-03-30
forum: Hardware
---

### Post by dpitch40 on 2012-03-30
I recently downgraded from Ubuntu 11.10 to 10.10 on my laptop (to get the old desktop environment with panel applets back), and now I have discovered that plugging headphones into my headphone jack doesn't automatically mute my speakers; I get some out of both my speakers and my headphones. In fact, I can't find any options to enable this. I have never had any problems like this before; not on 11.10 on the same machine or 10.10 on my old laptop, so there must be some option I'm missing to enable this. How do I do it?

---

### Post by Bill Z on 2012-03-30
You didn't mention what type of hardware you are using.   Many of the machines I work on have a disconnect in the headphone jack and it is not a function of the OS.  

Have you tried other ear phones?

---

### Post by Bill Z on 2012-03-30
Just saw this on another post.  Maybe it will work for you.

4. Headphone sensing and internal microphone. In default Ubuntu 11.04 on 722, when you plug your headphones, the sound from speakers isn't turned off and internal microphone isn't working. To solve these issues, download and install (by double-clicking on it):
Code:
[http://people.canonical.com/~diwic/temp/alsa-hda-dkms-acer3830tg_0.1_all.deb](http://people.canonical.com/~diwic/temp/alsa-hda-dkms-acer3830tg_0.1_all.deb)
This patch is actually for another Acer laptop, but I found that it solves the same problem on 722. There are however, two caveats for this. First, external microphone still isn't working, and second, if internal microphone still isn't working, you'll need to go to Sound preferences/Input and mute and then unmute microphone (to enable internal microphone, in Sound Preferences/Hardware "Internal Audio" must be selected, and "Analog Stereo Duplex" profile. On input tab, "Internal microphone" connector should be selected, and Input volume should be adjusted to about 100%). With this fix, Skype and Google Talk/Video work just fine. Details about this fix can be found at:

[http://bugs.launchpad.net/ubuntu/+so...ux/+bug/783582](http://bugs.launchpad.net/ubuntu/+so...ux/+bug/783582)

---

### Post by dpitch40 on 2012-03-30
I dual-boot Windows 7 on this machine and it works fine there; the speakers are muted when headphones are plugged in as you'd expect. So clearly there is no intrinsic hardware limitation. As a short-term solution, I can just listen on iTunes.

and please remember that I am using 10.10, not 11.04.

---

### Post by Yellow Pasque on 2012-03-30
Downgrading to Maverick is a band-aid solution. Support ends for it next month.
Anyway, try this to get latest alsa module:
```
sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
sudo apt-get update
sudo apt-get install alsa-hda-dkms
```

---

### Post by dpitch40 on 2012-03-30
I actually downgraded for other reasons, most because of the changes to the desktop environment but also because of some new bugs. (Including one with apt-add-repository) I've been using Maverick for years on my other machines and am totally satisfied with it.

Anyway, that did the trick; thanks!

---

