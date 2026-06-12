---
title: "Lost Audio after upgrading to Ubuntu 8.10"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by sanjeevpunj on 2009-03-30
Has this happened to others too? I am not able to play any sound after I upgraded to Ubuntu 8.10.In my System/Preferences/Sound I find my Audio card, but when I try to test the sound I get this message :-

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

As I am a noob with Ubuntu, I would like some help please, asap. 

Maybe I need to reconfigure something, but what something?

---

### Post by sanjeevpunj on 2009-04-01
I am adding some more info. The output of aplay -l at the terminal is pasted below:-
----------------------------------------------------------------------------------
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
--------------------------------------------------------------------------------
Hope this will help anyone reading this post.

---

### Post by sanjeevpunj on 2009-04-01
yet some more info. I ran this command to check if the sound card is recognised by the OS.

modprobe snd-card-ice1712

terminal returned this reply


FATAL: Module snd_card_ice1712 not found

Yet, I see that aplay -l gives me a list of sound devices, and my card is there, along with the motherboard's Intel device. I am wondering if Intel is grabbing the placve of my sound card.If that is so, how can I avoid using Intel devices?

Here's the output of aplay -l again

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
Subdevices: 1/1
Subdevice #0: subdevice #0

Cheers!

---

