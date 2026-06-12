---
title: "Sample rate problem?"
date: 2005-11-14
forum: General Help
---

### Post by Wordan on 2005-11-14
Hi

I am using a via82xx AC97 onboard soundcard on a gigabyte 7VAXP-Ultra motherboard with Ubuntu 5.10

Listening to Drone Zone from soma FM, It sounds as though it is being poorly resampled with very anoying whistling sounds(I notice it on some other sounds aswell, but not all). It sounds the same using Totem(xine) and Rhythmbox.

I did try creating a .asoundrc file using an example from the AlsaOpensrcOrg wiki to resample everthing to 48KHz which is the default rate for the sound card. (how do I tell what sample rate the card is set to?)
```
pcm.!default {
  type plug
  slave.pcm "dmixer"
}

pcm.dmixer {
  type dmix
  ipc_key 1024
  slave {
    pcm "hw:0,1"
    period_time 0
    period_size 1024
    buffer_size 4096
    rate 48000
  }
  bindings {
    0 0
    1 1
  }
}

ctl.dmixer {
  type hw
  card 0
}
```

I could read wiki's all day but my ability to understand alsa configuration doesn't come as quickly as I'd like and I don't understand exactly whats going on in that example. When I made this file and restarted rhythmbox, the sound stutterd badly.

Does anybody have any ideas about this?

(I have had a lot of problems with this motherboard, particularly with digital output to my 6year old Boston Acoustic digital speakers which came with a Gateway computer, and various windows driver updates messing them up even more with crackelling between sounds. And there are soooo many alsa settings for the card. This isn't really relevent to this post though :rolleyes: )

---

### Post by McQuaid on 2005-11-14
I am having the same problem since going to breezy.  Can't figure it out.  I also have ac97 but an intel8x0 chipset.  Never had an issue in hoary nor in my sid install.  Also I installed 1.09 alsa without issue in hoary so it's not that either.  I've just compiled 1.09a, b and even tried the latest rc.  All of them exhibited these sound problems.

---

