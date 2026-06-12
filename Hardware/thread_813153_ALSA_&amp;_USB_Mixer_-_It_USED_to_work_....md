---
title: "ALSA &amp; USB Mixer - It USED to work ..."
date: 2008-05-30
forum: Hardware
---

### Post by Brendo613 on 2008-05-30
Here's the deal.  On my Acer laptop, 82801H Intel audio chipset, I used to have no problem recording on Audacity through my Alesis USB mixer.  The mixer needed NO software / drivers, it just worked.  

After an ubuntu update, the mixer won't be recognized in Audacity.  lsusb shows "Texas Instruments" when it's plugged in.  If I cd /proc/asound/ and then cat cards, I get:

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0500000 irq 22

but no mention of this mixing board being plugged in.  I don't know if it used to be seen by the computer as a separate sound card or not.  All I know is I've been all over the internet the past few days trying to get it working again. So far ...
[LIST]
[*]Audacity's been re-installed
[*]Newest alsa driver, lib, utils, and firmware loaders have been installed
[/LIST]

This problem happened before, but I don't remember how I fixed it.  The mixing board works, and works great (look what I've done with it: [www.soundclick.com/brendanS](www.soundclick.com/brendanS) ).  Why did it stop?  More importantly, **how can I make Audacity see my board again?!** :shock:

---

### Post by Brendo613 on 2008-05-31
I now have three kernels installed.  

2.6.22-14 rt : usb mixer is recognized, records in audacity, but I have no sound playback.

2.6.22-14 gen : doesn't record, but sound plays back.

2.6.20-16 gen : record works, no sound playback.


I *think* the problem resides in the snd-usb-audio module, some part of ALSA.  Ideally, if I understand right, it is inserted into the current kernel (which can manually be done by sudo modprobe snd-usb-audio ?).  I have an older laptop with the 2.6.22-14.37 kernel, which through recent Ubuntu updates got bumped up to 2.6.22-14.38 on my new laptop used for recording, initiating all this hullabaloo. 

How do I get snd-usb-audio to work in the newer kernel?  It's useless as-is.  Please, any suggestions, any anything?  I'm really at a loss here.  It used to work, I just want it back how it was.

---

### Post by Brendo613 on 2008-06-02
bump.  I really need help, PLEASE

---

