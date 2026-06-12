---
title: "Will USB Laptop Speakers Work On Ubuntu Laptop?"
date: 2013-12-20
forum: Hardware
---

### Post by TomBrooklyn on 2013-12-20
Ubuntu 13.10 

Will a USB Laptop Speaker work on a laptop with Ubuntu?


I hear there might be issue with switching between built-in and USB speaker.      That it might require setting sound preference each time USB speaker is desired. 

I also heard some setup in Linux  PulseAudio might be required.    I'm not familiar with Pulse Audio.      Is it built in to ubuntu?     How does it work? 


One speaker I would like to get is the Kinovo LS210.      


[http://www.amazon.com/Kinivo-LS210-Portable-laptop-speaker/dp/B007R9RUPU/ref=cm_cd_al_qh_dp_t](http://www.amazon.com/Kinivo-LS210-Portable-laptop-speaker/dp/B007R9RUPU/ref=cm_cd_al_qh_dp_t)

---

### Post by ian-weisser on 2013-12-21
It's possible someone in this forum has the exact model you are looking at, but perhaps not likely.

My USB speakers do require an edit to Pulseaudio settings.
Pulseaudio is included with Ubuntu.

I use a udev rule to automatically change the settings when the speakers are inserted. Pulseaudio automatically changes the settings back when the speaker is removed.

---

### Post by Bucky Ball on 2013-12-21
Plug 'em in and see what happens! Take it from there ...

A USB speaker is a USB speaker I would have thought, but would be nice to hear the voice of experience on that particular speaker. The other thing is, of course, to do some research rather than relying on the fact someone here is going to have experience of this device (and then see your post anyway). I just had a quick sniff and I see no posts whatever to do with Ubuntu and this device. 

Meaning that it is either problem free or has never been used by anyone on Ubuntu, at a guess.

---

### Post by efflandt on 2013-12-22
When I use Plantronics wireless stereo headset with it own USB dongle, it is automatically recognized. Although, I manually select it as Output and Input in Sound Settings. I have not tried modifying a udev file to have it automatically switch to that. Ubuntu does automatically switch back to my other audio if the dongle is disconnected. Although, if analog is used for the headset, audio reverts to my analog stereo speakers and if the headset is used as digital, it reverts to HDMI when dongle is disconnected.

---

### Post by TomBrooklyn on 2013-12-24
> **ian-weisser said:**
> My USB speakers do require an edit to Pulseaudio settings.
Pulseaudio is included with Ubuntu.

I use a udev rule to automatically change the settings when the speakers are inserted. Pulseaudio automatically changes the settings back when the speaker is removed.

What is Pulseaudio, where in ubuntu would I find it, and how would I go about editing it ?

What is a udev rule and how would I get one implemented on my laptop?

Do I understand correctly that once you get this set up, you don't have to do anything to get sound besides plug the USB speaker in, or unplug it to return to built-in speakers?

---

### Post by TomBrooklyn on 2013-12-24
> **Bucky Ball said:**
> Plug 'em in and see what happens! 

to do some research rather than relying on the fact someone here is going to have experience of this device (and then see your post anyway).
I don't own USB speakers yet.    I am researching to find a solution to my audio needs.   This thread is part of that research. 

I want to see if USB speakers work with ubuntu.     If few here have experience with USB speakers with ubuntu, where better ought I look?

---

### Post by TomBrooklyn on 2013-12-24
> **efflandt said:**
> When I use Plantronics wireless stereo headset with it own USB dongle, it is automatically recognized. Although, I manually select it as Output and Input in Sound Settings. I have not tried modifying a udev file to have it automatically switch to that. Ubuntu does automatically switch back to my other audio if the dongle is disconnected. Although, if analog is used for the headset, audio reverts to my analog stereo speakers and if the headset is used as digital, it reverts to HDMI when dongle is disconnected.

What does the USB dongle do?    Transmit to the headset?

If it is automatically recognized, why do you have to make a manual selection?      Do you have to make this selection every time you plug in the dongle? 

What is the difference between analog and digital use of the headset? 

What is HDMI and how does that differ from regular built-in speaker operation? 

============
I am hoping to get a speaker that works instantly when I plug it in.    Not one that requires  adjusting software settings every time I plug it in or take it off.

---

