---
title: "Noise when using glxgears, other GL screensavers"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by Belyel on 2006-08-23
I'm running Ubuntu 6.06 686smp on my Acer Travelmate 8200 laptop.  I'm pleased with the performance of the smp kernel and ubuntu in general, and my problem is more of an annoyance than a serious issue.  When running any of the GL screensavers, my hardware makes noise.  It's not fan noise, and can range from a high pitched tone to a series of clicks that seem to be in time with the frame rate.  I looked at [this topic]("http://www.ubuntuforums.org/showthread.php?t=73593&highlight=noise+screensaver"), but that is a bit impractical given the sealed nature of my laptop.

The noise is not present when playing UT2004, but it is when i'm using xgl with compiz.  The noise is also not present in winxp using 3d screensavers or playing any of the other games I play (ie oblivion, doom3, need for speed, etc). I know the games likely use directx, so it may not be an indicator of the problem at hand.  It does not seem to matter if the laptop is plugged in or running on battery power.

Any suggestions for eliminating this noise would be helpful in quieting my office and desk at school.  Thanks in advance.

---

### Post by Belyel on 2006-08-24
I played around with my computer to see what I could do about this issue, and still haven't solved it, but here's some more info:  I tested to make sure it was not dependant on whether the laptop was plugged in.  It happens both on AC and battery.  I am now certain it is connected to the framerate of whatever is rendering on screen.  GL screensavers that render at ~100fps or above make noise, if I drop the rate down to below that, it becomes inaudible (though I'm quite certain it's still moving something).  As it is obviously a hardware problem, I guess I'm looking for anyone who also has this problem and what they did about it.

---

### Post by drdnl on 2006-10-08
Maybe of some use, my screen "buzzes" when I run it at 1600x1200@100hz. But its a crt, I have no idea whether lcd's can do the samem try setting sync to vblank in order to avoid hight fps.

Might help, could just be time to call Acer :)

-D

---

### Post by Foxen on 2006-10-20
Actually, I have the same kind of noise in my laptop when running fgl_glxgears and glxgears so it's not just your comp, I've had it on desktop machines as well but usually all the fans in such a system will make the noise inaudible... Don't think it's anything to worry about...

---

### Post by d3v1ant_0n3 on 2006-10-20
Ok this is odd...I've been getting this 'noise' with one of the animation plugins in Beryl...I thought I was going mad...

---

### Post by Henry Rayker on 2006-10-20
I got a strange buzzing on my desktop when running this screensaver as well.

However, when I unplugged my speakers, I got no more buzzing. I was using the live cd, however.

---

### Post by Belyel on 2006-11-03
> **Foxen said:**
> Actually, I have the same kind of noise in my laptop when running fgl_glxgears and glxgears so it's not just your comp, I've had it on desktop machines as well but usually all the fans in such a system will make the noise inaudible... Don't think it's anything to worry about...

I contacted ACER, but since they don't support linux, I didn't get a lot of help from them.  It's been buzzing/humming since I installed Linux and no problems so far.  It's probably some capacitor or wiring on the video adapter that's causing some magnetic field affecting the speakers (conveniently located right on the front of the computer).  Or something.

> **d3v1ant_0n3 said:**
> Ok this is odd...I've been getting this 'noise' with one of the animation plugins in Beryl...I thought I was going mad...

Nope, but it will drive you nuts eventually.

---

### Post by NTolerance on 2006-11-07
> **d3v1ant_0n3 said:**
> Ok this is odd...I've been getting this 'noise' with one of the animation plugins in Beryl...I thought I was going mad...

Which plugin?  I've had this problem for months and there is very little information about it.

---

### Post by impman89 on 2006-11-08
I'm having this same problem - and its quite bad. It only started when i installed xgl/beryl. I have the TM8200 with the ati x1600 card. It sounds like the card emits a high pitched sort of clicking noise. This does not happen when I'm not using xgl/beryl.

I've noticed it a little in windows in the past, but not nearly as bad, and a lower pitched sound. The only time it happened in windows was when scrolling in Firefox and a few other times. Right now with xgl on, it seems to be nearly constant. It's particularly bad when firefox is open.

---

### Post by noxxle on 2006-11-16
Ive got the same issue, doesnt happen so much in compiz. If i use beryl i can make the sound by rapidly minimizing and maximizing a window.

---

### Post by NTolerance on 2006-11-30
Are any of you guys using earbuds when you experience this problem?  I had the problem before with that setup until I tried a set of regular headphones w/ volume control.

---

### Post by Belyel on 2007-02-07
With my machine, it is definitely not coming from the speakers or headphones.  It is a hardware problem that remains unresolved despite my having my computer rebuilt by Acer a couple months ago.  Anything that requires 3D acceleration with openGL causes the noise.  I don't think that it is a serious issue, but it is common to Linux and Windows (try an OpenGL screensaver in windows and see what I mean).

---

