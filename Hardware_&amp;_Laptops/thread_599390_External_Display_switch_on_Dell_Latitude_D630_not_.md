---
title: "External Display switch on Dell Latitude D630 not working"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by harley_frog on 2007-11-01
I have a new Dell D630 that I use for work, running Ubuntu 7.10.  Overall, I am very happy with the performance (Compiz-Fusion works great, can even play Alien Arena with no problems), but I do have one small nit to pick.  I am a librarian and often do instruction on using library resources.  The CRT/LCD toggle ( Fn+F8 ) is not working.  I have the i8k module installed and running and selected and even pick Dell Latitude laptop under the Keyboard setting and still no joy.  Does anyone know a way to get the toggle to work?  Ideally, I would like to have both CRT and LCD displays on at the same time.

Thanks.

---

### Post by qwill on 2007-11-07
Have the same kind of problem.
X11 works out of the box while using the internal DFP and the laptop undocked.

When docking; I would like to have X11 on the 2 external displays ( Dell 2007fp) one analog, one digital.

what's happening is that the internal DFP is still on when docked; and black screen on the other.

I use the nvidia driver. with twinview enabled.
I tried to use the nvidia-settings switchs but no success.

I guess the answer is on the xorg.conf file; under the screen section (?)
I tried to add the following line under the screen section :

Option "Display"  "BIOS" 

but was unsuccessfull too...

Its a shame as this is the only thing that prevent me from switching completely from XP to Ubuntu ...

Has anyone mastered the D630 with ubuntu/linux ?

Qwill

---

### Post by qwill on 2007-11-13
Got some progress ...
Got one of the external monitor (the one connected via VGA working; but the one dvi-connected powers off ...
Xwindows start on the internl screen and on the CRT (while docked)...

I attached the xorg.conf for info ...

---

