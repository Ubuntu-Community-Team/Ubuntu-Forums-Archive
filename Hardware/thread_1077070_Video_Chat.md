---
title: "Video Chat"
date: 2009-02-22
forum: Hardware
---

### Post by 3dmatrix on 2009-02-22
I wish to do video chat over yahoo or msn. I do not know how to do it. In fact I do not know how to use the webcam in Linux. I am new to all this. I earlier used to use Mepis but could not use it there also. I tried to open Ekiga and can see my self in the video window but do not know what to do next. Please help. I am also unable to record sound using the inbuilt microphone or capture sound in Linux. Where as all this is possible in the same computer in Xp.

---

### Post by SketchyClown on 2009-02-22
We all want to be able to do video chatting over MSN.

Some clients like **aMSN**,** Kopete**,** Mercury **have some level of video capability, but no audio.

**Skype** for Linux has audio/video but you can't go on MSN on it.

[http://www.justskins.com/open-source/video-chat-on-ubuntu/920](http://www.justskins.com/open-source/video-chat-on-ubuntu/920)

That site tells the tale of video chat woe on Linux, thus far.

As for your sound, I'm assuming you can hear sound, so maybe all you need to do is to go into your **Volume Control** and un-mute the microphones.

HTH.

---

### Post by binbash on 2009-02-22
I suggest installing and using amsn for video chat @ msn

---

### Post by 3dmatrix on 2009-02-22
I tried to record sound using audacity but it didnt work.
There was simply no responce from the mic.
My front mic boost is full.
How can i check if i can record a movie with my webcam, just to make sure its working well with the audio.
My terminal responce is as below :
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Unknown device 011d
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

---

### Post by 3dmatrix on 2009-02-23
I added the following line to my /etc/modeprobe.d/options file
options snd-hda-intel model=acer position_fix=1 enable=yes
after rebooting i can record sound from the inbuilt mic but only in Audacity and even there the quality is very poor. In other applications like the sound recorder or Cheese there is only a continues tak, tak, tak, tak sound recorded.
Can any one help ?

---

### Post by soltanis on 2009-02-23
God, more sound problems...

You are most likely (I am sure) using pulseaudio. I have no idea why Ubuntu insists on using this, because it really causes more problems than it solves, but before we get rash and start uninstalling things,

try this

```

sudo apt-get install alsa-utils

```

then

```

alsamixer

```

When you're in alsamixer, press tab so that [Capture] is highlighted in the top left corner. You'll probably see a bunch of stuff, but using the arrow keys, select "Internal Mic" or something similar and hit spacebar,
so that L ____ R CAPTUR is written above it.

Then hit escape and try recording again.

---

### Post by 3dmatrix on 2009-02-26
Alsa mixer was already installed
I configured it as you advised
Recording is possible but quality is extremely poor.
Its as good as no recording.
There is a lot of noise.

---

