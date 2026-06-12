---
title: "No audio via speakers - headphones work fine"
date: 2019-02-17
forum: Hardware
---

### Post by sf6 on 2019-02-17
Hello,

I have a Panasonic CF-SX3 Haswell based notebook with Ubuntu 18.10 running.
My problem is, that I can't get the speakers to work ootb. Here is the alsa script output: [http://www.alsa-project.org/db/?f=5d7f5e88afe88255d5a4f42e8618d09a8e2e0453](http://www.alsa-project.org/db/?f=5d7f5e88afe88255d5a4f42e8618d09a8e2e0453)

Let me explain my findings using alsamixer so far:
1. When I plug in my headphones, the channel automatically switches  to the unmuted headphones' channel. Speaker channel is then muted as it  is to be expected. The headphones work just fine.
2. When I unplug my headphones, headphones' channel gets muted and the speaker unmuted, as one might find perfectly reasonable. But there is no sound coming out of the speaker.
3. After some messing around with the channels, I found out that it's *not* the speaker's channel that produce sound via the speaker,  it's also the headphones' channel (with the physical headphones unplugged). That means: When I *manually* unmute the headphones' channel,  the speaker works just fine. For some reason, it seems the headphones' channel is wired for  two outputs at the same time.

How can I fix this?

Thanks :)

---

