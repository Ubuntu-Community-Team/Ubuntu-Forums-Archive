---
title: "Dual AMD R9 280x - Video Lag in Wily"
date: 2015-11-04
forum: Hardware
---

### Post by jamal7 on 2015-11-04
Hello all

I've recently installed 15.10 server 64 bit on my machine. It has 2x Radeon R9 280x at PCI 1&3. I'm experiencing video lag on youtube on both screens inidvidually. Actually in the firefox tab with video, when I have it selected, the whole system is laggy until I switch windows. Full screen on both together causes freeze or blackout. 

Let me try to explain further: it's not actually the video thats lagging in the case of youtube html5. the video plays fine, but the mouse cursor disappears while it plays and I then lose lucid functionality in the system. Trying to pause or go back a page lags out the whole browser. This is in normal size or full screen. Similar problems in VLC, but the video there will actually lag occassionaly.

Mupen64plus works smoothly oddly enough. So do other games via Wine.

I've turned off swap. 8 gb of Ram. Using Xinerama. i3-wm. Any ideas? Thanks

Jamal

---

### Post by gordintoronto on 2015-11-05
What Desktop Environment did you install? Did you install a proprietary video driver?

---

### Post by QIII on 2015-11-05
Right at the moment, installing the fglrx driver would bork the system.  There is a bug causing some grief.

---

