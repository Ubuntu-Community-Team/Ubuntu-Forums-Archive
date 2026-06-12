---
title: "Speaker problems"
date: 2012-03-21
forum: Hardware
---

### Post by tomopotamus on 2012-03-21
Hey everyone,

My laptop has developed a problem with its sound/speakers this afternoon.  The problem is that the speakers aren't working anymore.

When I plug in my head phones everything is fine.  The speakers themselves just aren't working.  I hope there is something that I can do to rectify this problem!

I did some snooping around just now and I saw that I should run the command aplay -l, which I have, and here is the output:


tom@tom-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


In addition my laptop is a Fujitsu AH530.

Are there any other commands that I should run that would be helpful?

Thanks in advance!

---

### Post by tomopotamus on 2012-03-21
I just ran two more commands that I've found trying to solve this problem.

Maybe the output will be helpful in trying to solve this problem:


tom@tom-laptop:~$ cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC269
Codec: Intel IbexPeak HDMI
tom@tom-laptop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

---

### Post by smiggy on 2012-03-22
Good luck with getting answer on this buddy.
Intel HDA based sound is Ubuntu's achilles heel.

I have exact same issue on my Panasonic CF52 and multiple posts have yielded zilch in response.
I guess the hope is if you ignore it long enough it'll go away!

I wound up buying an external speaker that plugs into my headphone jack before binning Ubuntu completely.
I keep checking back on similar posts like yours to see if they've made any progression.
Pulseaudio I think is the problem.
I got sound output via the speakers using OSS but had trouble making the config stick.

---

### Post by tomopotamus on 2012-03-22
It's good to know that I'm not the only one that has a problem like this!

The weird thing is that my sound works fine if I plug in headphones and listen through them.  The speakers just don't work.  I'm hoping that they're not broken!

If worst comes to worst though I'll just have to buy external speakers and that shouldn't be a problem.

---

