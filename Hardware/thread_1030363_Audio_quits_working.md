---
title: "Audio quits working"
date: 2009-01-04
forum: Hardware
---

### Post by relambert on 2009-01-04
Hello all,
Having a problem with the audio on my system. Doesn't seem to matter what application I'm using at the time either. Stops while using rythmbox, or streaming a video or radio in Firefox. If I'm using Firefox at the time, it will lock up and I have to force quit it. Seems to be real random. Can go hours without a malfunction and then it will happen every couple minutes. Am posting output from lspci -v so you can see the audio chip.

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Elitegroup Computer Systems Unknown device 1878
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at d800 [size=256]
	I/O ports at dc00 [size=64]
	Memory at fb101000 (32-bit, non-prefetchable) [size=512]
	Memory at fb102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

Did a fresh install not long ago, and it was doing it before then too. Thought about updating the drivers, but don't know how. Could anyone walk me through this procedure or offer any solutions?

---

### Post by sonicb00m on 2009-01-04
I just had exactly this problem. I think it lies in some updates for pulseaudio and alsa.

I have totally uninstalled pulseaudio and now things have returned to a more stable environment.

---

### Post by gettinoriginal on 2009-01-04
Here are some sites that may help:  :P

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506),
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012),
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by relambert on 2009-01-07
Wanted to update this post. After following the instructions from many of those threads, I 've made some progress, but only with video. WMV now streams nicely and my dvd's will play. Still can't watch Quick Time mov fiiles, but that's not that big of a deal. Problem is, my sound still stops. Most of the instructions that I read seem to deal with "no sound" issues, but my audio works "most" of the time. Adding all the different mixers, setting up pulse audio, changing the default sound card have not helped. What's strange is that if I do nothing else with the computer, just let whatever is playing, play, it doesn't seem to happen. 
Oh well, the computer functions fine, except for that, so I'll try to keep plugging away.

---

### Post by relambert on 2009-02-06
This issue may be resolved, although it's not quite the way I thought I was going to have to do it. I disabled the onboard audio and installed another stand alone sound card. So far, so good, it hasn't quit. If anyone else has this issue, this may be your only option.

---

