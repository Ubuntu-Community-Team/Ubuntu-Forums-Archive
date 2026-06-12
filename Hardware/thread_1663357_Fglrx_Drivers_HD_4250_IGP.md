---
title: "Fglrx Drivers HD 4250 IGP"
date: 2011-01-09
forum: Hardware
---

### Post by psience7 on 2011-01-09
I am using a HD 4250 IGP, I .deb'd the latest fglrx drivers, installed them successfully and successfully did an aticonfig --initial setup, and checked the info, and it looks like it installed correctly but I am getting bad 2d performance, and with compiz enabled its even worse, anyone know about these?

---

### Post by coffeecat on 2011-01-09
Did you have a specific reason for installing the proprietary fglrx driver? My HD4200 in my laptop and HD4350 in desktop both run compiz just fine with the open source driver in Lucid/10.04 and later versions of Ubuntu.

---

### Post by psience7 on 2011-01-09
I tried the open source with the same exactly result, without compiz, 2d is not reaching its full potential, and very slow if compiz is on. Same with proprietary either from ati's site, or in the repo. I tried messing with Xorg a bit with some suggestions like adding some certain Options with no luck. I reinstalled a few times. Even without compiz, scrolling is somewhat slow/jerky and if I am watching a movie in Totem and try to drag its very laggy. When I use this card on Windows its quite overkill for just 2d apps on a 1920x1080 monitor but on Linux its very sub-par and a bad user experience, and also Flash and Gnome System Monitor can use up to 60-70% of a Quad Core CPU, that is about (3) 3.2ghz cores maxing out just to handle a flash video or scroll system processes... And I have tried several versions of flash, even my amd64 version, etc. Also several browsers. This is about the 3rd rig I've tried Ubuntu with and I always have serious issues.

Could you recommend a good piece of graphics hardware that runs VERY well on Linux? Is there some sort of consensus on this issue? I am getting very conflicting results across Google.

---

### Post by coffeecat on 2011-01-10
I can only say that my HD4350 with the open source driver copes very well with compiz and flash and I've played HD videos fullscreen on my 16:10 1920x1200 monitor (obviously with black bars top and bottom) without problem. The GPU specifications on this link might explain the difference between your and my experience:

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units)

I'm out-of-date in my experience with nvidia, but a later chipset with the proprietary driver might be the answer. Perhaps others might recommend specific cards.

---

### Post by gradinaruvasile on 2011-01-10
Flash:

Flash uses acceleration, but NOT decoding (meaning that the cpu wil decode the stream). The upcoming 10.2 series use some hardware decoding that will probably work on vdpau on nvidia and 4xxx series uvd2 capable ati cards. I tested on nvidia and hardware decoding works (but it is buggy). So, faster cards help only up to a certain point. Keep in mind the fact that flash player has nothing to do with your installed codecs, it lives in its own world.
And the flash player player from the sites in question may differ - some are optimized some not. Some have low cpu even in higher resolutions, some use cpu like crazy even on 240p.

Movie players:

Totem is the worst one of them - it is slow. Really.

The best bet for ati 4xxx cards is libva + latest vlc with gpu decoding enabled = hardware decoding via the vaapi interface that uses the cards uvd2 decoding capabilities.
You have to install libva1, vainfo and the xvba-va-driver packages. Run vainfo in a terminal to confirm that it is working.
In vlc tick the "use gpu acceleration" checkbox under input and codecs and set "skip h264 deblocking filter" to "all". At the video section select "xvideo output" as output device.
I can confirm that vlc can use libva succesfully on nvidia, but i havent tested it on 4 series ati.
Other than that smplayer is a very good player, i use it because it can use the vdpau decoding on nvidia (that is much better than libva/vaapi). And has lower cpu usage that vlc even with plain xv output.

I recently had a computer that i built for someone with radeon 3000 igp in it and i played around with it. I had no problems with video play or anything, but with opengl/3d it did not reach the 8200 (igp) stability and compatibility, despite having higher frame rates.

Advice:

Use nvidia + its proprietary driver if you want stability ( i had 1 freeze in the last year), compatibility (3d games, both native and via wine work best on them) and performance.
I use nvidia cards on Linux, and had no issues (use Linux for 3 years). They work better than any other model out there. Just use the proprietary driver.
The and the 8200/8300, 200 series and up  cards  have very good hardware decoding capabilities (vdpau). I can play 1080p movies with 5-10% cpu.

---

### Post by psience7 on 2011-01-10
I am just going back to Windows 7, I don't have time for all this **** constantly. Maybe I'll tailer some hardware and try Arch sometime.

---

