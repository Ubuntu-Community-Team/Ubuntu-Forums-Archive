---
title: "M-Audio Quattro USB Sound"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by mortram on 2005-05-07
I'm trying to get my USB 4x4 Quattro sound card working in Ubuntu, but unsure of where to start.  The device seems to be detected by the Ubuntu installer, but the sound is very grainy and choppy.  Also, when I try to run "Volume Control" it tells me "No volume control elements and/or devices found."  Ideally, I'd like to explore multitrack recording within the linux world but it seems I need to do some configuration first.

In Kubuntu, the mixer was unavailable but the audio was not grainy and distorted (??).  Why should this be?  I'm enjoying the Gnome DE and would prefer to get my hardware up and running without having to switch back to Kubuntu.

---

### Post by SFN on 2005-05-18
Try [this](http://ubuntuforums.org/showthread.php?t=30891). The actual drivers, of course, will be different but it **might** help.

---

### Post by 23meg on 2005-05-18
i have a quattro as well, and am using it without trouble for non-JACK (=non-pro) purposes at the moment. i've had [some initial trouble](http://www.ubuntuforums.org/showthread.php?t=21851&highlight=quattro) , but swapping ports and deciding not to use the device via  a usb hub helped. i've been curious about the mixer issue as well, and found out that the quattro has no internal mixer device of its own, and that's why it doesn't get a mixer device entry. if you used it in windows you should be aware that it only has a main volume control there as well. 

this is in fact logical, since the interface is intended for pro use where separate outs will be mixed with another mixer or used independently anyway, and software volume control will handle them in pro applications (in fact any application where you can assign ALSA software volume control). and no mixer circuitry means less noise and better output fidelity.

about the choppy sound: are you using the quattro via a usb hub? do you know what brand your usb controller chips are? do your usb ports have their own independent irq channel?

---

