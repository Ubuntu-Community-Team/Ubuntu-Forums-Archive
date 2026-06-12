---
title: "Earphone not recognized when plugging in"
date: 2017-06-12
forum: Hardware
---

### Post by trungnb on 2017-06-12
Hi, been working on 16.04 for a year and ignoring the problem. Recently I need to use Ubuntu 16.04 on my lap in office so it's uncomfortable for me to work without music. So anyone with expertise or experience please help me to make the headphone jack works. The music goes keep go out of the speakers when earphone plugged in (instead of being played in earphone). Here is the alsa info link as people usually post when asking the same question:
```
http://www.alsa-project.org/db/?f=ace62220cc16bff75492df425de6e92b40584bde
```
Thanks all in advance,
Trung

---

### Post by ajgreeny on 2017-06-12
Go to your volume icon in the panel and from there to **Sound Settings**.

This will open **pulseaudio-volume-control** where you can firstly check that the volume settings for headphones are high enough.  All devices listed in the **output devices** tab are set separately in the drop-down box so you should see both speakers and headphones listed.

That may not solve your problem of the sound still coming from the speakers when headphones are plugged in, but it may allow you to mute the speakers separately; both working together simultaneously sounds like a hardware setting or fault as normally speakers are muted when headphones are plugged in so check any hardware manual you have for that.

---

### Post by Yellow Pasque on 2017-06-13
Try toggling these values in alsamixer (and also check pavucontrol after you do that as ajgreeny suggested):

```
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
```

If it doesn't work, you may need to look at updating your kernel audio modules: [https://github.com/torvalds/linux/commit/b5337cfe067e96b8a98699da90c7dcd2bec21133](https://github.com/torvalds/linux/commit/b5337cfe067e96b8a98699da90c7dcd2bec21133)
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by trungnb on 2017-06-21
> **Temüjin said:**
> Try toggling these values in alsamixer (and also check pavucontrol after you do that as ajgreeny suggested):

```
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
```

If it doesn't work, you may need to look at updating your kernel audio modules: [https://github.com/torvalds/linux/commit/b5337cfe067e96b8a98699da90c7dcd2bec21133](https://github.com/torvalds/linux/commit/b5337cfe067e96b8a98699da90c7dcd2bec21133)
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
Thanks, this works for me!

---

