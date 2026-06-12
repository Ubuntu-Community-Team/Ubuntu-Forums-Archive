---
title: "Intrepid Ibex probs with Creative SB Xfi 5.1 USB soundcard"
date: 2009-04-02
forum: Hardware
---

### Post by nagyon ribanc on 2009-04-02
Hello all,

After being of linux for a bit I finally return, and gladly so.
However I can not get the soundcard to work at all. Though I believe I have installed all that is required, it still gives me no sound, which drives me a bit crazy. (can't handle silence for to long :D) 
Running on a 4GB Vaio from the NS-11 series. And as suggested by the title of the post with the latest version of Ubuntu available. 
Terminal gives the following
> 
me@my-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: S51 [SB X-Fi Surround 5.1], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: S51 [SB X-Fi Surround 5.1], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any help to get this thing running is appreciated.

Also when I try to get the sound settings properly "System -> Preferences -> Sound" and try the usb soundcard setting, the following error shows up:
> 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.


Erwin

---

### Post by ntrgc89 on 2009-09-19
bump

---

