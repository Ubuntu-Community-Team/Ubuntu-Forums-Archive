---
title: "Kworld DVB-T USB 323UR - no sound"
date: 2012-01-17
forum: Hardware
---

### Post by madvinegar on 2012-01-17
Hi to all.
I need some help in order to make the above TV usb stick fully functional. (ubuntu 11.04)

This is the whole story:
In the begining I could not get the card to work. Even if it was seen by lsusb, the TV applications (tvtime, xawtv etc) could not see it.
The driver was em28xx which was already installed.
I ran dmesg and found the following line: error: firmware xc3028-v27.fw not found.

So I searched through the internet, found this firmware, downloaded it and copied it to /lib/firmware file.

Restarted the laptop and managed to get the tv card actually working. I installed Tvtime, scanned and found all the available channels.

The problem is that I cannot get the sound to work. I have tried too many options and more specifically:

I have gone through the /etc/tvtime/tvtime.xml file and started to mess around with the <option name="MixerDevice" value="default/Line"/> line.

As I understand the "default" goes for pulse audio and the "Line" goes for the bar that you use to increase/decrease the volume.

At first the volume bar at TVtime was not moving at all (it was stuck at 0). After changing the "default/Line" to "default/Master" I got the volume bar in TVtime to move (together with the volume of my laptop) but I got no sound.

I also installed gnome alsa mixer and changed the tvtime.xml line to "hw:0/Line" or "hw:0/PCM" or "hw:0/CD". (hw:0 activates the alsa application). In all cases the volume bar of TVtime was moving and I could set it to maximum, but I don't get any sound...

I have installed also pulse audio volume control, played around with the options, and still no sound...

Needless to say that I was unmuting all options and setting all bars to maximum.

I tried also XawTv, but apart from the fact that I don't like it, I don't get any sound either.
I tried Kaffeine, but even if the channels are scanned, they are not saved so I don't have a list of channels.

I like TVtime (even if I can only get analog channels while my card is for digital channels as well) but I cannot figure out how to get the sound working...

At this point I am open to suggestions and I would like to thank you in advance for your kind assistance.

---

### Post by madvinegar on 2012-01-18
I did it !!!!! YEEEEEEAAAAHHHHHHH !!!!!            

I did it with Kaffeine !!!!! Which is better because it receives digital channels!!!

I had to change the scan options to:

tuner timeout ms: 5000
source: autoscan with 167khz offsets

All the proper channels were found, and they work GREAT. Picture is great, sound is great!!!!

I CANNOT BELIEVE IT! I finally did it !!!!!

I am getting the hang of Linux pretty good!

Please mark this topic as solved !

---

### Post by syerges on 2012-01-18
this is the third time I've read that... now that you have your 50 beans... I hope you stop.:confused:

---

### Post by madvinegar on 2012-01-19
> **syerges said:**
> this is the third time I've read that... now that you have your 50 beans... I hope you stop.:confused:


hahaha, sorry for that. I don't even know how the "beans" work.

I posted it three times in different sections because it was a major problem that a lot of linux users have with the Kworld DVBT cards.

I have searched through the internet 100 times and no-one had found a proper solution.

(either no sound, or distorted sound with delays etc).

This is why I made the same post in 2-3 topics as I wanted it to be seen and assist people with the same problem.

I am verry sorry if I overflooded the threads.

---

