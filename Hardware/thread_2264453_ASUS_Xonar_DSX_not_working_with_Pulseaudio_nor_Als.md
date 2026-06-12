---
title: "ASUS Xonar DSX not working with Pulseaudio nor Alsa"
date: 2015-02-07
forum: Hardware
---

### Post by SWATLLAMA on 2015-02-07
I read a thread from 2013 on the Ubuntu forums and from later 2013 on the Mint forums covering this. From those, I was told to use this: [http://permalink.gmane.org/gmane.linux.alsa.devel/100921](http://permalink.gmane.org/gmane.linux.alsa.devel/100921)
However, I'm not sure how to apply that patch. So far as I can tell, there is no alsa-devel in the repositories.
One of the threads concluded that on newer kernal versions, this sound card should work. I'm on 3.13 and it's not being detected.

Any help?

---

### Post by Yellow Pasque on 2015-02-07
The patch was accepted into kernel 3.8.x, so unless you're using an older kernel, there's no need to apply it. 

Maybe more is needed than the patch: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1093958](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1093958)

---

### Post by JDorfler on 2015-02-19
Hmm, odd.  Mine works like a charm.  What does ```
lspci -v
``` give you?  You should get something like this;
```
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 7100
	Flags: bus master, fast devsel, latency 0, IRQ 52
	Memory at f7f00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
```

Of course your system will say something different.  Like AV100 or AV66.

Also, when you boot up disable your onboard sound on the motherboard.

Also, use ```
alsamixer
```
There, make sure you use the F keys to navigate to see if you can find your card to play with the settings of your card.

---

