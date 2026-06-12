---
title: "VIdeo playback stutter"
date: 2011-03-04
forum: Hardware
---

### Post by Clastir on 2011-03-04
Hi all 

I am running Ubuntu 10.10 on a Samsung Q30 with Mobile *Intel*® *945GM* Express Chipset. 
When playing video the first 20 seconds or so is fine but then it stutters almost as if there is a problem when a buffer fills or some thing.
I have tried Mplayer and VLC and both do the same thing. 
This si my first visit with Ubuntu ( and linux for that matter ) and im loving it, SO much faster than any other OS i have tried. 
But this one thing is spoiling the experience. 

I would be grateful of any suggestions ( doesnt seem to be Mobile *Intel*® *945GM* Express Chipset driver in my synaptic package manager ) and please be gentle 

Cheers

---

### Post by Clastir on 2011-03-07
Forgot to mention it works fine under xp on the same machine

---

### Post by Afishionado on 2011-03-07
Try running "mplayer -vo help" to get a list of video output drivers that mplayer understands. Then try "mplayer -vo <driver from the previous list> <filename>" to explicitly set the video driver. Try all the likely video modes and see if any play noticeably better.

(Also, the aa and caca drivers are fun but mostly useless.)

---

