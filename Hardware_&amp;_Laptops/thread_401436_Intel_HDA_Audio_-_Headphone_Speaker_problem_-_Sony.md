---
title: "Intel HDA Audio - Headphone Speaker problem - Sony Vaio"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by hornett on 2007-04-04
I have a Sony Vaio VGN-C1Z/B laptop, with a sound chip that needs the snd-hda-intel driver.

It works, but I have to manually mute the speakers if I want to use headphones, or the sound comes out of both! 

Slightly embarassing if you forget to disable it and have it blaring out of the speakers while you're sitting there on a train, unaware because you have headphones on...

One thing I noticed, in dmesg, there is the following line:
```
hda_codec: Unknown model for ALC262, trying to auto-probe from BIOS...
```

But I can't work out how to force it to use a specific model...

Any ideas?

Ta

PS. I'm running Feisty. :) Great distro!

---

### Post by teaker1s on 2007-04-05
There is an alsa config file for settings, but the issue you have is a known alsa issue with this model sound chip. I too had it on Debian and it was fixed with an updated alsa-so now sound from speakers mutes when headphones connected.
Annoying as it is your choices seem to be wait for updated alsa in repositories or compile latest version

---

### Post by onbongos on 2007-04-05
fwiw, i used to have problems under windows too - i would get sound out of the speakers, but nothing out of headphones

---

### Post by hornett on 2007-04-08
Ok, thanks for your replies. I'm going to have another search on Launchpad and file a bug if I can't find any.

---

### Post by mikewhatever on 2007-04-08
Compiling your own version can help. Here is how
[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)
A newer version of alsa has been out since the guide was written, the latest is 
alsa-driver-1.0.14rc3

---

### Post by hornett on 2007-04-09
Built and installed alsa-utils, driver and lib, but I get exactly the same result.

I've tried various options for the model=option but nothing seems to make any difference. I still get exactly the same line in dmesg:

```
hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
```

I've googled some more, and come to the conclusion that support for this chip is rubbish on most operating systems, apparently I'm lucky to get anything out of it at all!

:confused:

---

