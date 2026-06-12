---
title: "Probably?? Overscan problem. Not correct output to TV in 1360X768"
date: 2011-05-03
forum: Hardware
---

### Post by deckoff on 2011-05-03
I use Thinkpad x 40 laptop with LG 16:9 LCD TV as a media center. When I set the resolution to 1240x768 and stretch the picture to 16:9 mode ( a TV option) all is ok. All icons and all look stretched, which is normal, cause the PC is outputing 4:3 picture, and mode is 16:9.
When I use 1360:768 option, though, (picture mode 16:9), the icons and menus look as expected, but the whole picure is kind of moved up ad left, part of the picture is cropped ( the one shown on TV) and there are black borders right and down.
Is this overscan? Any ways to fix it, tried some xorg.conf settings, with no luck, tried xvidtune, but it starts but spits errors and does nothing.

I use Xubuntu 10.10, but my other laptop( the same, but with Kubuntu 10.10) has the same problem, my girlfriend laptop (Toshiba with XP) shows acts even worse...
Any ideas how to fix it?

---

### Post by GROwen on 2011-05-04
I'm having a similar problem to this and it's driving me nuts.

see my other thread [here]("http://ubuntuforums.org/showthread.php?t=1748124") for details. Unfortunately no-ones been able to offer any advice as yet.

I don't believe this is overscan because of the amount of the output that is outside of the screen.

I haven't pursued the xrandr option as yet as I was hoping to find a thread (that I mistakingly forgot to bookmark and is now eluding me) that covers options for altering xorg.conf. argh!

This might be helpful though, I'm going to give it a shot tonight.

[http://en.gentoo-wiki.com/wiki/Nvidia_HDTV](http://en.gentoo-wiki.com/wiki/Nvidia_HDTV)

---

### Post by deckoff on 2011-05-06
Some of the problem was resolved with buying a new a cable. Now the TV recognizes that there is input from the PC. The PC offers me more resolutions to choose from. Still, I dont get the one I want and I would have probably to add it manually. 1360x768 and others does not display correctly, according to the manual I should use 1366x768 and I will try to add it manually.

---

