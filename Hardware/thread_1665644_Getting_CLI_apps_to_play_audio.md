---
title: "Getting CLI apps to play audio?"
date: 2011-01-12
forum: Hardware
---

### Post by tacticalbread on 2011-01-12
I'm having trouble getting CLI apps to play audio; SIDplay for example, wants to use /dev/dsp, which doesn't exist on my system.

My sound card is at /dev/snd/controlC1, but when I make a symbolic link at /dev/dsp, it yells about "/dev/dsp: Inappropriate ioctl for device" and I have no idea what that means.

I don't think it's the problem, but I'm using my Alesis MultiMix USB as my soundcard (USB Audio Interface). Although when using the built-in soundcard (which is at /dev/snd/controlC0), nothings any different.

So how would I get SIDplay to play right, through my audio interface?

---

