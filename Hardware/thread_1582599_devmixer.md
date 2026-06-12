---
title: "/dev/mixer???"
date: 2010-09-26
forum: Hardware
---

### Post by vlajkoral on 2010-09-26
Just installed 10.10, and everything worked fine. Install xawtv for my TVcard WinFast 2000XP, it worked, but without sound. So I started xawtv in terminal and it say "**open /dev/mixer: No such file or directory**"
So where is /dev/mixer on Ubuntu 10.10???

---

### Post by markackerman8@gmail.com on 2010-10-20
I have the same problematic error trying to run tvtime ... arggghhhh!

Mark

---

### Post by Yellow Pasque on 2010-10-21
/dev/mixer is the mixer device used by OSS. I'm not too familiar with xawtv, but you probably need to change audio output to ALSA/pulseaudio in some configuration dialog/file. Either that, or use padsp to emulate the OSS device.

---

