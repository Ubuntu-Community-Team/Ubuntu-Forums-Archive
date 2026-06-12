---
title: "Setting up Hauppage TV Tuner Card"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by veraction on 2005-09-26
[B][COLOR="Red"]OK, it seems to work. I fixed it by appending these 2 lines to any file (actually did some alsa file, heh) in /etc/modprobe.d/ : ```
options bt878 card= tuner=50 gbuffers=4
options bttv radio=0 card=10 tuner=50 gbuffers=4
```These settings seem to work for my particular card (Hauppauge WinTV-Go-Plus Model 1033 (you might need diff settings). i'll let you know when it breaks & I can't figure it out[/COLOR][/B]Ok, I've never set up something like this before on linux so am clueless (plus I hadn't even heard of tv tuner till a few days ago)

Anyways, it is a Hauppage WinTV-Go-Plus module 1033 tv tuner. It works fine with Windows XP (except the remote) -- so hardware is good.

How do I set this thing up? I installed tvtime via apt-get & am able to receive one channel (ch 4.), but no other channel. If I change channels, it still has same thing. I've done Setup -> Channel Management -> Scan for channels in tvtime (right click), but still same thing.

Any ideas?

I've been googling for a few hours now & don't see anything.

Some things I already have installed (by default installation)... and recognized..

```

$ modprobe -l | grep bttv
/lib/modules/2.6.10-5-386/kernel/drivers/media/video/bttv.ko

$ modprobe -l | grep tuner
/lib/modules/2.6.10-5-386/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.10-5-386/kernel/drivers/media/video/tuner.ko
/lib/modules/2.6.10-5-386/kernel/drivers/media/video/tuner-3036.ko

$ lspci | grep Capture
0000:01:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:01:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)


```

I also tried installing xawtv to see if that worked, & that doesn't receive any channels at all. All I see is black screen & this is output on terminal:
```

$ xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.10-5-386)
WARNING: v4l-conf is compiled without DGA support.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_OVERLAY(int=1): Invalid argument

```

[edit] by the way, I seem to have gotten MythTV to actually show video (no audio-tvtime has audio) & probably doesn't do a number of other things. **however, mythTV can only display 1 channel as well.**

---

