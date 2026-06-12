---
title: "Acer 5920 headphone/SPDIF jack"
date: 2009-08-11
forum: Hardware
---

### Post by Bartender on 2009-08-11
Three questions - does anyone know for sure if the headphone/spdif jack on the front of the Acer 5920 is digital or optical sp/dif?  The manual doesn't say and I've spent hours googling.  I'm sure it's easy to tell if you're an expert on sp/dif connections but I'm not that guy.

Second question - Vista has a function to change the audio default from speakers to sp/dif output.  I don't see anything obvious in Ubuntu.  Anyone know how to activate the sp/dif output in Linux?

I tried booting into Vista and setting sp/dif as the default.  The speakers quit but I didn't see visible light inside the jack while playing a CD.  Some info on web indicates you should be able to see light, others say no.  Because I can't see light in Vista, I don't know if it's working or not in Ubuntu.

Here's the results of aplay -l:

**** List of PLAYBACK Hardware Devices **** 
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0

EDIT 8-19-09:

SP/DIF output appears to be working now.  I say "appears" because I only got results just last night, and only true 5.1 when using VLC. Turns out the headphone jack is optical.  I bought a cable with an optical 3.5 mini jack at one end and standard TOSLINK at the other.  Tried MPlayer, Totem Player, and VLC but got no sound out of the ONKYO TX-DS474, nor indication on the ONKYO's front panel that it was seeing any input.  Found this on the "internets":

[http://lists.medibuntu.org/pipermail/admin/2009-April/001028.html](http://lists.medibuntu.org/pipermail/admin/2009-April/001028.html)

Followed the link to Luke Yelavich's PPA:

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

Added his sources and key, then updated.  Turned on the ONKYO before turning on the laptop - have no idea if that makes any dif but that had been mentioned in some posts.  VLC audio set to "Use SPDIF if available" as per some other posts.  Popped "Brotherhood of the Wolf" DVD into the Acer 5920.  The receiver's display indicated "DOLBY DIGITAL" just like it does when playing a DVD in the Sony DVD player, and all speaker channels made noise.  Whoo-hoo!!

However, the signal would drop out every 10 seconds or so.  I screwed around with volume sliders and enabling/disabling various playback settings in the Ubuntu volume control - nothing seemed to help.  Sliding volume to zero didn't make any dif either.  That was mentioned in several posts.

Tried MPLayer, then Totem Player.  Both of them made noise too, but the ONKYO display dropped back to "Dolby Pro Logic" and stereo output.  Played around with audio settings in both players but could not get 5.1.  Doesn't necessarily mean it can't be done, I have a feeling I just didn't hit the magic combination.

Went back to VLC, and this time the audio was not dropping out during the exact same part of the DVD that had played before.  Don't know why that would be, but I did reseat the cable between the first and second try - maybe the 3.5 mini jack wasn't inserted all the way?

Anyways, Luke Yelavich's tweaks to PulseAudio seem to be working for me.  Luke, I love ya, man.

---

