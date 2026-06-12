---
title: "Intermittent sound that doesn't last long (LG P1 pro Express Dual)"
date: 2008-11-04
forum: Hardware
---

### Post by Hydraah on 2008-11-04
Hi all!

Long time reader, never really posted.

So far I have rarely needed to use sound under ubuntu however it is becoming increasingly annoying not being able to listen to music, or hear a youtube video on my laptop.

I'm running 8.10 but this has been a problem since I first put ubuntu on this laptop (7.04 I think).

Basically, it'll intermittently have working sound if I use "options snd-hda-intel model=6stack-dig" into the alsa-base file, intermittently as in every time I reboot. When it does decide to work, it'll work for a few minutes, whether or not there is any sound, and eventually fade out.. but not a smooth fade, a crackling fade out. It's almost as if a buffer is getting filled up completely but I have no idea how/why. 

The model is identified as ALC883 accoring to aplay -l. I have run through all the options available (there are a lot of them!) and 6stack-dig worked the best.

lspci -v shows this:

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: LG Electronics, Inc. Device 005f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d8500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

aplay -l:

```
 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Is there anything else that I can do? I have tried changing the rate from standard (48khz I think?) but this usually resulted in no sound at all.

I have probably missed some useful part of the troubleshooting information too - please let me know if I have and I'll grab it asap.

Thanks heaps!!

---

### Post by Hydraah on 2008-11-04
Tried many different sound troubleshooting guides, none of which fixed this problem.

I think I had the sound working ages ago using a fairly early version of Fedora, but the later versions have no sound at all.

---

### Post by FrankT-Qc on 2009-03-26
Hi there !

Same Laptop, same problem... Gusty, Hardy (32 and 64), Intrepid (32 and 64 bits), Jaunty Alpha (64 bits)... Stock kernel, custom kernels whatever, it made no difference (note that I have never made any effort to solve this problem while messing arround the kernel, just to mention it's not an architecture thing)

Oh, by the way, I DID goole the problem too and found a few hundred solutions messing around with hda_* and model=* ...  none has worked for me either, even those that suposingly had worked on the very same laptop... 

Note : I have perfectly working sound out of the box with OpenSUSE (10 and 11) and if I work a little, I also do with Debian (Lenny), Fedora (9 and 10) and DSL... It looks like an Ubuntu thing... Still, it's surprinsing that it works with Debian and not Ubuntu...

First thing off, you might have noticed that with Ubuntu, the headphone jack is working perfectly... Plug in external speakers and you're into business (by the way, the mic jack isn't working either, get yourself a USB mic...)

Here's my **_ugly_** solution to have sound on the laptop speakers under Ubuntu when my life depends on it (if you're going to try to convert a friend to Ubuntu, you need sound !) : Boot Debian (OpenSUSE makes sound easier, but I don't like green) and virtualize an Ubuntu guest... eheheheh (seriously, don't do that... but it works !!!)

Here's another thing that could help us meanwhile : While the headphone jack provides perfect sound, in the first minutes after boot, the laptop speakers are alive and eventually go through this slow distorted death (capacitor saturation i'd say) which I don't want to hear. Anyone has an idea on how to shut the laptop speakers ? I tried most swith configurations in the gnome sound applet and none works.

Thanks

Francois

---

### Post by Hydraah on 2009-03-26
OH - so glad I'm not the only one having this problem.

So maybe we can find out why sound works on OpenSUSE and Debian, and work from there.

---

### Post by markbuntu on 2009-03-27
That is definitely and ALSA driver problem. That said you could maybe try the Debian alsa debs and see if they fix it.

---

### Post by ruchita.sen on 2010-10-01
Hey I am having the same problem...
I am using Fedora 10... and i used to get intermittent sound for like 20-30 seconds and then it was gone...
I plugged in my headphones and now i get sound externally... not in my headphones...

Could you guys find out the solution?

Thanks for the help..

---

