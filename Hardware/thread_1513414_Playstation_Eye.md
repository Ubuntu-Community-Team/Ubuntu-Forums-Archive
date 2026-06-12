---
title: "Playstation Eye"
date: 2010-06-19
forum: Hardware
---

### Post by riskbreaker927 on 2010-06-19
So here's a thread about the Sony Playstation Eye, which is a spectacular webcam that almost works on Ubuntu, but not quite.

Particular complaints:

-On my desktop, which runs Lucid 64 bit (2.6.32-22), any program that attempts to use the microphone on the PS Eye freezes. As you should know, the way this is done is by having the PS Eye plugged in at boot time, and then selecting it through the pulseaudio volume control under input. If this is done, and then you attempt to use any program to record sound or even VoIP, the program will freeze. This does not happen on my netbook, which runs Lucid desktop 32-bit (should be the same kernel.)

-On both machines, the imaging from the camera works, but I am unable to record video. On my netbook, it records about a second's worth of frames and then freezes until I click stop; on the desktop, I get highly garbled frames most of the time. They slightly resemble the correct image, but are garbled - as if chunks of one frame are being used in the next one. Very strange behavior.
 
-For what it's worth, the issues reported above happen with the driver shipped with Ubuntu. I have since (on my desktop) compiled and installed the driver available at [http://bear24rw.blogspot.com/2009/11/ps3-eye-driver-patch.html](http://bear24rw.blogspot.com/2009/11/ps3-eye-driver-patch.html) , and while it did make the improvements discussed on that page, it did not fix the problems above.

-Also, for what it's worth, I think these issues may have started with Lucid, because I don't think they happened in Karmic. But I didn't use Karmic in 64-bit mode, so I am not sure.

Let's try to knock some heads together and find a way to fix these problems, eh?

---

### Post by riskbreaker927 on 2010-06-19
Also, for some reason although saving videos does not work, streaming them via VLC does.

---

