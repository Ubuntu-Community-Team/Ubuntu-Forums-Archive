---
title: "MacbookPro6,2 hda-intel sound distortion"
date: 2011-03-20
forum: Hardware
---

### Post by smallpawn on 2011-03-20
Hello,

I fixed this once, but can't remember nor find the solution again. 

I'm using Kubuntu Maverick. 2.6.35-28 kernel.

Sound is distorted when playing high pitched sounds. I think the solution last time was by adding a line to /etc/modprobe.d/alsa-base.conf. BUT adding options snd-hda-intel model=mbp55 at the end of that file doesn't work for me.

The last time I had this problem was using ubuntu (gnome), now I'm using Kubuntu.

If someone can help me please, I'm quite screwed...

Thank you.

EDIT:

```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
``````

sudo dmidecode -s system-product-name
MacBookPro6,2
``````
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: Cirrus Analog [Cirrus Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Cirrus Digital [Cirrus Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by smallpawn on 2011-03-21
Ok, so I managed to solve it. The problem was in part because I was only getting sound from one channel. I paste the solution from [my blog]("http://sm4llpwnr.blogspot.com/2011/03/ubuntu-macbookpro-sound-problem-solved.html"):

I had a problem and because of [Pidgin]("http://www.pidgin.im/") sounding distorted, I was looking absolutely at the wrong direction...

**The Fake Problem **
My laptop was sounding bad, and when I received a message in Pidgin it  sounded awfully distorted on high pitched sounds. That's why I thought  my problem was ONLY distortion. Well, it was not.

**The Real Problem**
After rebooting zillions and millions of times, compiling different alsa  drivers with different options, I suddenly gained the perfect power of  great listening. With this power I was able to hear that only one  speaker was working. Huh, was the mixer not mixing the damn thing right?  No idea, but something like that. So I added this line to the  /etc/modprobe.d/alsa-base.conf file:
[FONT=&quot]options snd-hda-intel model=mbp55[/FONT]

Rebooted and... the sound came from the two speakers!!! Excellent. Now,  Pidgin still sounded awful. What the heck was with Pidgin? Ok ok, we  also have a solution for that. In Pidgin go to:

[FONT=&quot]Tools > Preferences > Sounds[/FONT]

In method, select "Command". Then at the top of the screen, in the Sound command field write:

[FONT=&quot]play %s[/FONT]

If this doesn't work, maybe you don't have "play" installed, it was my case in Kubuntu. Type in a terminal:

[FONT=&quot]sudo apt-get install play[/FONT]

Now open a pidgin conversation and click on Options, make sure "Enable  sounds" is checked. Sound should we working wonderfully now in Pidgin  and the whole system!

---

