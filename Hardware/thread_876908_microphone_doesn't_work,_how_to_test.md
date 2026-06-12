---
title: "microphone doesn't work, how to test?"
date: 2008-08-01
forum: Hardware
---

### Post by clarezoe on 2008-08-01
I'm struggling with my microphone, it can't catch any sound, I'm sure it's not broken, it works fine in my windows machine.

I used audacity to make a record, no error information, but no sound can be captured. See screenshot.

And also used skype to make a test call, I can't hear my own voice.

I've been search this solution for a few days, nothing helped. I don't know how to make a troubleshooting of a microphone, anyone knows?

My sound card is intel, and I'm using Alsa driver the latest version.

```
$ lspci|grep audio
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
```


I don't know where to check it.

It's really annoying, any help and suggestions are appreciated.

Thanks

/clarezoe

---

### Post by sergiom99 on 2008-08-01
make sure you have it selected as your input device and that its volume is set high.
In Kubuntu i can do that by double clicking the sound icon in the taskbar. Should be the same in Ubuntu.

Good luck.

---

### Post by clarezoe on 2008-08-01
Thanks!
Here is my volume control, which is you said the sound icon.

See that in the playback tab, the microphone is muted, and it should be, in case I also unmuted it, but no help at all.

---

