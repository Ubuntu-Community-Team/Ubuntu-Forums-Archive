---
title: "Inspiron 1525 (x3100 graphics)"
date: 2008-11-06
forum: Hardware
---

### Post by maxinstuff on 2008-11-06
First of all, hi everyone. I am completely new to Ubuntu and Linux so please be nice :)

I ordered a new inspiron 1525 as this seems to be the model that Dell ships with Ubuntu in Europe and the US (I live in Australia where we are all forced to pay the microsoft tax), but now I see that the onboard graphics (intel x3100) may entail some driver issues.

I have searched around and can only find documentation on older versions of Ubuntu. My question is this, has anyone tried ubuntu 8.10 on this hardware, and if so, has the driver issue been resolved? 
 
Does compiz work properly? Also, is it only compiz that is affected or 3d rendering in general?

---

### Post by razel_elvin on 2008-11-10
hello Maxine my Names Razel I'm from the Philippines and right now I am using Dell Inspiron 1525 and has x3100 graphic adapter. well, I'm still new in ubuntu and I purchased it that has vista installed on it and I hate it, so i downloaded ubuntu 7.04 then upgraded to 8.04 and works fine with compiz fusion, my only problem is my wireless card. broadcom but it will be resolve there are threads for that. while compiz is working fine. so recently I upgrade to ubuntu 8.10 and its good. i dont get any problems at all. it works fine. Hope you got yours too. good luck. =)

---

### Post by maxinstuff on 2008-11-11
Sounds like good news :)

There must have been a fix developed and ut into the final version of 8.10.... 

All the threads on this seem to start and finish before the final release of 8.10, it is all reports from people using the beta.

Weird that I can't seem to find anyone saying, "this is now fixed, yay!"

From what you have said though, things look good.
I will update this thread once my laptop arrives.

---

### Post by softtower on 2008-11-11
I have a Lenovo Thinkpad  T61 with Intel X3100 and Compiz works great. Everything is crazy fast and smooth. The only issue is somewhat slow (but nothing serious) scrolling in Firefox, but this browser is well known for being terribly inefficient in Linux.

Ironically, my newer laptop that uses Intel X4500HD card, is about 4 times slower in Compiz than an older X3100 but this hopefully will be addressed by newer drivers.

---

### Post by foolink on 2008-11-11
I've been experiencing problems with X3100 and 8.10 (Intrepid). The most noticable problem is low GL performance, and also playing high definition video with mplayer (Tried with video output: xv, x11 and sdl).

No problems in Hardy though.

Related information may be:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/262758](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/262758)

---

### Post by maxinstuff on 2008-11-17
Ok, so I got my laptop today and I am pleased to say that so far everything works out of the box :)

I did try putting the desktop effects on high and it DID cause some issues, but the effects that caused it were not ones I want anyway. I don't really need my windows to warp and change shape when I move them around.

On the default settings everything seems to work just fine.

I have yet to run into any real issues. It's only day 1 though I guess :P

---

### Post by maxinstuff on 2008-11-17
I have noticed that when I move windows around it doesnt seem to move "smoothly" (not sure the correct word to describe this). They seem to drag a bit? 

Is this normal? I remember a previous work computer had this issue and I was told the graphics drivers must be out of date. It is not a major issue, but it makes me mildly annoyed. Anyone know if this can be rectified?

---

### Post by maxinstuff on 2008-11-19
Ok, I just tried to run the Gnome chess game in 3d mode and it did not work!

I got the following error:

"You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support"

This is no good. I want to look good while getting beaten horribly at chess by a computer. 

Does anyone have a fix for this? Is it possible to get my 3d acceleration working?

---

### Post by maxinstuff on 2008-11-24
bump

---

### Post by bobe84 on 2008-12-01
If u use smplayer go to :
[http://smplayer.sourceforge.net/downloads.php?tr_lang=en](http://smplayer.sourceforge.net/downloads.php?tr_lang=en)
u have fresh smplayer and mplayer, so far i didnt have any problem with smplayer and HD videos.
Using intrepid/kde 3.5.10 from unofficial repos

---

### Post by maxinstuff on 2008-12-08
Ok, so my 3d acceleration looks like it works, but not really.

I can get glxgears to work, and the framerate goes nuts when it is minimised which im told means that it must be hardware accelaration being used.

I also installed Neverwinter Nights (linux native) which works quite well on the highest settings.

Chess still wont go into 3d mode though. I get the same error as above. So from that I guess that maybe most of it works but some features arent available (driver issue?). Why can my computer run neverwinter nights and not a 3d chess game???

---

