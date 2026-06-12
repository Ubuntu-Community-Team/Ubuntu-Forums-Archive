---
title: "Audio-in combo jack not recognized"
date: 2012-01-29
forum: Hardware
---

### Post by BigRedButton on 2012-01-29
I have recently bought an Asus Zenbook UX31 and I am having two (unrelated) issues with it. The wifi connectivity is intermittent for no good reason, and the audio-in combo jack is not recognized by alsa.

The Zenbook has a TRRS jack instead of having separate "headphones" and "mic" jacks. I have a TRRS 1/8" to 3x RCA splitter to test it with and the output works just fine but the input doesn't switch to it when I plug in the cord as it would with a separate mic jack.

In alsa there is no way I have ever seen to manually switch between the mic input and the built in webcam mic, or between the headphones and built in speaker; it is switched by detecting the presence of a plug. My lay assumption is that the presence of a plug in the combo jack is treated as being a headphone plug and switches the speakers to use it (which it does) but that it is waiting for another plug to switch the mic to use the jack.

That said, IS there a way to tell alsa to use either the built in mic or the mic jack? Choosing between "Analog Input" and "Analog Mic" in the sound settings does nothing.

The Zenbook uses the Intel HD Audio chip, common in laptops.

---

### Post by msundman on 2012-03-13
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/950490](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/950490)

---

### Post by SorryGoFish on 2012-04-02
Confirmed.

---

### Post by SorryGoFish on 2012-04-02
I managed to get my TRRS connector working by adding the following line to `/etc/modprobe.d/alsa-base.conf` (because a line with the same prefix did not exist already):

```
options snd-hda-intel model=laptop-dmic
```

I'm not sure if this is a good idea though. I have not tested with HDMI out.

---

### Post by Yellow Pasque on 2012-04-02
This might help too: [http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

---

