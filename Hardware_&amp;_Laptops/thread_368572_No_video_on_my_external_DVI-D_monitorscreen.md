---
title: "No video on my external DVI-D monitor/screen"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by forteller on 2007-02-23
I've been searching all over the place for a solution to this very annoying problem but no luck. I've seen a threads on this topic with no replies, and I have no idea why that is, but please reply to this, if only with a link to where I can find a solution, that is much better than nothing!

I have a Acer laptop (Ferrari 4005) with a ATi Radeon X700 graphics card. I have successfully connected my external monitor with the DVI-D cable and I have no problems except for this: No matter what kind of video I play, or what kind of media player I use to show it, no video plays on the external screen! They always play on the laptop screen, and the media player is just black on the external screen. If I try to connect with the analog cable the video plays on both screens, but the resolution and quality of the external screen is terrible!

If you know how to fix this, please let me know, I'll be forever grateful!

I don't know if it's relevant, but my resolution is 1680x1050, and my external screen is a 22" Chimei CMV 221D.

EDIT:
Some more info:
I am currently on Feisty Fawn Herd 4 x86, but I had the same problem on Edgy x86.
Two times I have managed to get the video to play on both screens. I had to first open the lid of the laptop before I started playing the video, but after it had started playing I could close the lid without the video disappearing from the external screen. One of these two times I was also able to keep on watching another video after the first one had ended without having to open the lid again. The other time that didn't work.

---

### Post by forteller on 2007-02-25
I got it! Finally!

Since it's been so hard for me to find the solution, I'm thinking maybe someone else might be struggling too, so here's what I did:

First you install the newest fglrx drivers from ATI: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Then you open terminal and write
```
aticonfig --query-monitor
```
You will get a list of your connected monitors. One is the internal monitor, the other is the external.
Now you write:
```
aticonfig --enable-monitor=[name of one of the monitors]
```
If that makes your external screen go black then you do the same thing again, only this time with the name of the other monitor.

Voila! Your internal monitor goes blank and you can now watch as many videos on your external monitors as you want!

I can't believe I had to struggle so much to figure this out. I've been looking for a sollution to this for so long! Why isn't there a easy howto out there on how to do this? That is one of the things the Linux community has got to do for non-geeks to be able to switch!

---

### Post by maschbaer on 2007-03-01
Hey Thanx,

This helps a lot!!! I wasn't able to turn of my internal notebook screen while I connected an external one. So I never was able to watch movies on my large scren.

By the way, if the external screen is removed, does it switch back to the internal screen? What happens if you afterwards reconnect the external screen? Does directly disable the internal screen and activates the external?

Bye Jan

---

### Post by mgashop on 2007-09-21
Great that you found the problem.  I have same problem but I don't understand the steps you took to fix it.  Where to I find the stuff to edit?

I'm running XP on dell latitude laptop.  My lcd went out and I have it hooked up to an external monitor and it will not play video.  It isn't a codec problem as everyone states.  Video worked fine before the lcd screen went out.

Any detailed help would be greatly apprecated.

thanks
mgashop

> **forteller said:**
> I got it! Finally!

Since it's been so hard for me to find the solution, I'm thinking maybe someone else might be struggling too, so here's what I did:

First you install the newest fglrx drivers from ATI: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Then you open terminal and write
```
aticonfig --query-monitor
```
You will get a list of your connected monitors. One is the internal monitor, the other is the external.
Now you write:
```
aticonfig --enable-monitor=[name of one of the monitors]
```
If that makes your external screen go black then you do the same thing again, only this time with the name of the other monitor.

Voila! Your internal monitor goes blank and you can now watch as many videos on your external monitors as you want!

I can't believe I had to struggle so much to figure this out. I've been looking for a sollution to this for so long! Why isn't there a easy howto out there on how to do this? That is one of the things the Linux community has got to do for non-geeks to be able to switch!

---

