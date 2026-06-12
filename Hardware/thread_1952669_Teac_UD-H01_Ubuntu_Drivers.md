---
title: "Teac UD-H01 Ubuntu Drivers"
date: 2012-04-04
forum: Hardware
---

### Post by nossifer on 2012-04-04
I have already googled but found nothing.  I bought a DAC and it doesnt recognize in Ubuntu.  Other DAC's have recignized fine so I just assumed.  First time in many years this has happened.  I have emailed the manufacturer and can update this thread accordingly.  

I don't know what is involved to write drivers, but there are Win/Mac ones out there:  [http://www.teac.eu/hifi-audio/reference-series/h-01/ud-h01/](http://www.teac.eu/hifi-audio/reference-series/h-01/ud-h01/)
I assume there is no way to compile these other drivers for Ubuntu?  

Here is wishful thinking.  Hopefully I don't need to wipe that box and make it windoze.  I'll cry an entire box of kleenex if I have to.

---

### Post by channelzero on 2012-07-02
I'm thinking of getting one of these myself to connect to a raspberry pi, seems that a fix (the bug is in the usb chip it seems) has been created for the linux usb implementation in upstream kernels. The details of the patch are here (one line!):

[http://www.spinics.net/lists/linux-usb/msg65620.html](http://www.spinics.net/lists/linux-usb/msg65620.html)

I'm rebuilding openelec for raspberry pi with the patch applied, if your handy at building custom kernels you can apply it yourself to build a custom usb kernel module for ubuntu or request that it gets applied in a future kernel release (not sure of the procedure there).

---

### Post by father_ted on 2012-07-31
Just brought one of these home and plugged it in. works without any issues. sounds LOVELY.

PS. startign to fiddle with pulse to get some upsampling happening

---

### Post by emi_dm on 2012-08-12
> **father_ted said:**
> Just brought one of these home and plugged it in. works without any issues. sounds LOVELY.

PS. startign to fiddle with pulse to get some upsampling happening

So, it works with Ubuntu? I mean, there's no need to do anything "special" apart from plugging it? Today I went to a hi-fi shop and the seller told me so, but I've read some posts indicating there was actually some trouble.

I have the Music Streamer II and have absolutely no problem with Ubuntu 11.04. I'd like the TEAC to be trouble-free as well, but I am a bit puzzled by the contradictory comments I've been reading so far.

Thank you so much.

Regards,

---

### Post by father_ted on 2012-09-25
I must recommend using the later pulse package from 

[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu)

the dac now switches frequency as i change audio source. im still putting everything through pulse - but video now most changes the dac to 48k and most audio apps back to 44.1k. 

the re-sampling in pulse is not great and makes a fair bit of cracking when its in a bad mood. or most of the time. 

i'm also doing some gaming while playing spotify and its is working perfectly.

i hope in 12.10 we get all the latest audio packages as this will allow better re-sampling and 24bit audio with pulse. alsa 1.0.24 which is in use with 12.04 is from the previous ice-age and needs a refresh. i don’t seem to be able to find a reason why we are still using the elderly alsa - im guess kernel versions are the cause.

---

### Post by Jack Kelly on 2012-12-18
Just wondering if anyone has tried the Teac UD-H01 in Ubuntu 12.10?  I'm seriously thinking of buying the UD-H01

---

### Post by sailor05 on 2013-01-01
> **Jack Kelly said:**
> Just wondering if anyone has tried the Teac UD-H01 in Ubuntu 12.10?  I'm seriously thinking of buying the UD-H01
I use it with Ubuntu 12.10.  For music, I use the ALSA interface with Audacious and XBMC, as I want bit perfect output to the DAC. The device i choose for ALSA is hw, so no processing is done to the signal. 
Audacious and XBMC work perfectly on all sampling rates from 44 to 192k, no noise and you will see on the DAC the sampling rate it is receiving is the same as the sampling rate of the file being played.

This arrangement "kind of" works with some other music players, but only if the music files have sampling rates of 44 or 48k. This happens with Amarok, where anything over 48k is distorted.

---

