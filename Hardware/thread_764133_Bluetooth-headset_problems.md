---
title: "Bluetooth-headset problems"
date: 2008-04-23
forum: Hardware
---

### Post by Romi on 2008-04-23
Hi,

I tried to install my bluetooth-headset (Sony Erricson HBH-PV702, System is Hardy). After some connection problems, it works fine now (with blueman). It is connected now, but does not schow up anywhere in the system (volume control etc.). The only thing I got working is when I enter the following line, I can hear myself in the headset: "arecord -D bluetooth -f S16_LE | aplay -D bluetooth -f S16_LE"!
This is the content of my ~/.asoundrc:
```
pcm.bluetooth {
	type bluetooth
	device "00:18:13:F9:20:F0"
	profile "auto"             #optional, supported profiles are: auto, hifi and voice 

}
```

So, how can I get the system to output the sound on my headset instead of my "normal" speakers and use the mircophone of the headset? Theoretically, I have to change the used device somewehere, isnt it? But where? Or is there just something I can wrap around applications where I can specify antoher device (this would be enough for my needs)?

thanks in advantage, 
Roman

---

### Post by Romi on 2008-04-25
No ideas? I'm getting despair of it :(

---

### Post by oscar on 2008-04-25
You can try changing "pcm.bluetooth" to "pcm.!default" but sound won't work while the headset is disconnected.
I'm still playing around with mine so will post back if I get it working properly.

---

### Post by Romi on 2008-04-27
> **oscar said:**
> You can try changing "pcm.bluetooth" to "pcm.!default" but sound won't work while the headset is disconnected.
I'm still playing around with mine so will post back if I get it working properly.
Mh. I chaned it to "pcm.!default", but it doesn't change anything, Sound still comes from my normal Soundcard.

I have to clue about it :confused:

---

### Post by derailed1 on 2008-04-27
I used gtbsco in gutsy and it worked awesome.  But in hardy nothing.  Im thinking of switching back.  I hope we can get this to work soon!

---

### Post by randomAccess on 2008-04-28
Hm, I can see the device but fail to connect to it. I even tried to edit audacious config file but could not find line pcm_device. TRied to add that line, but audacious deleted it after initiation.:confused:

Amarok is another story. When I switch to ALSA, both mono and stereo text fields are not-editable. :confused:

Any ideas???

---

