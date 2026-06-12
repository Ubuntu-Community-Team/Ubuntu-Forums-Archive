---
title: "Sound Cards, Multiple Sounds don't work"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by statictonic on 2007-11-02
I have tried a large number of onboard sound cards and other various generic sound cards.  All seem to exhibit the same issue in Ubuntu.  There's often difficulty with two programs playing sound at the same time.  For example having XMMS running and playing UT2004.  (i think they both use OSS)

However there is one sound card I have come across that will let me have a billion things running if I want and never give me a problem in Ubuntu.  It's an old Sound Blaster Live 5.1 card that I have.

Is the problem of not working with multiple programs producing sound at the same time common with sound cards, and the Sound Blaster Live 5.1 cards just have excellent compatibility?

---

### Post by Dodger73 on 2007-11-03
ALSA can be a strange beast. Try configuring dmix similar to the example below (which is my ~/.asoundrc for my integrated NForce4 audio):

```
#for 5.1 speakers
pcm.ch51 {
	slave.pcm "dmixed"
	slave.channels 6
	type route
	ttable.0.0 1
	ttable.1.1 1
	ttable.4.2 1
	ttable.3.5 1
	ttable.2.4 1
	ttable.5.3 1.0
#	ttable.0.0 1.0
#	ttable.0.0 1.0
}

pcm.my_card {
  type hw
  card 0
  # mmap_emulation true
}

pcm.dmixed {
  type dmix
  ipc_key 1024
  #  ipc_key_add_uid false   # let multiple users share
  #  ipc_perm 0666           # IPC permissions for multi user sharing (octal, default 0600)
  slave {
	pcm "my_card"
	channels 6
	rate 48000
  }
}

pcm.dsnooped {
  type dsnoop
  ipc_key 2048
  slave {
  pcm "my_card"
  #   rate 48000
  #   period_size 128
  }
}

pcm.asymed {
  type asym
  playback.pcm "ch51"
  capture.pcm "dsnooped"
}

pcm.pasymed {
  type plug
  slave.pcm "asymed"
}

pcm.dsp0 {
  type plug
  slave.pcm "asymed"
}

pcm.!default {
  type plug
  slave.pcm "asymed"
}
```

Notice how pcm.!default pipes into pcm.asymed, which pipes into ch51 which pipes into dmixed and sets up a routing table for the channels. The routing table may vary on your system - use "speaker-test -c6" to figure out which channel belongs to which speaker and set up the ttable entries accordingly. 
There's not much in-depth documentation on what the different keywords in the alsarc actually mean and how to use them, so the above is googled together from various searches, but works fine for my machine. Notice that you may have to increase buffer sizes for various applications, as for me, sound started crackling when I enabled this config. Hopefully PulseAudio (or Phonon for the Kubuntu users) will solve these problems in a less convoluted way.

---

