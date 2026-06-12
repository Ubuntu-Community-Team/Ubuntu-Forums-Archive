---
title: "Sound Volume Changing issues"
date: 2005-03-23
forum: Hardware &amp; Laptops
---

### Post by Firetech on 2005-03-23
I feel so alone with this problem, I haven't found any solution anywhere... I just hope you guys can help me.

Here goes. I recently installed Hoary (finally, after too many years of windows...), and have configured it slightly to my needs (most of the hardware works). Although, from the very beginning, the sound volume has been a bit problematic. When I change the Main volume, nothing happens (the same with both OSS and ALSA mixers). I can, however change the volume using the PCM channel (Both) or the Headphone channel (just ALSA). Is there any way to make the main channel work?
I'm running a manually configured kernel compiled with make-kpkg, and my soundcard is integrated on my motherboard (lspci gives "0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)", which is correct according to the motherboard manual).

Right now, I'm not sure if Main volume changing works in the default kernel, but I will test right now and post the result here in a few minutes...

The reason I need the Main volume changing is not the volume control applet, but my multimedia keyboard (and yes I have read the wiki post about Multimedia keyboards), which won't change the volume with any program. I haven't fully tried out metacity, but I prefer to have an OSD telling me what the volume is. Such as the one I see when I use the default hotkeys system or the program (package) Hotkeys.

And, one more thing, Ubuntu rocks when you get used to it! :D

---

### Post by Firetech on 2005-03-23
I have now checked if the Main volume worked with the default Kernel, it didn't.
I also forgot to say that the kernel I'm running is 2.6.10.

---

### Post by agds on 2005-08-01
Perhaps you've solved the problem by now, but there's a thread on this topic entitled "Desktop Volume Control Problem."  Some solutions have been suggested, but nothing for the OSD issue, which has also bothered me.

---

