---
title: "Problem viewing youtube videos (the video speeds up)"
date: 2009-04-25
forum: Hardware
---

### Post by billyboy1978 on 2009-04-25
Hello.
Today I experienced a very strange issue with jaunty.
I started a video in youtube, and the video was playing twice as fast as normal(?) wth is going on?

The same thing with both firefox and konqueror.

Installed: kubuntu-restricted-extras and flash from adobe.com
This does not happend with Ubuntu 9.04, only Kubuntu.

Another thing is that I had to install java for youtube sound at all.

I had this issue with 2 different machines both with nVidia geforce 8200/AMD sempron (32 bit)



Someone havin' a solution for this?
Thanx in advance

---

### Post by James78 on 2009-05-23
Finally, someone with the same issue as me. This happens to me with ALL flash videos. I've reinstalled countless times and it's still happening. I've also noticed that it seems to be apparent not only flash, but other videos as well (VLC, etc). Kubuntu 9.04 Jaunty...

Related: [http://ubuntuforums.org/showthread.php?p=7329402](http://ubuntuforums.org/showthread.php?p=7329402)

---

### Post by whoop on 2009-05-23
Is it something like this bug: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/360746](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/360746) ?
If yes, then it is reported.

---

### Post by James78 on 2009-05-23
Would it help if I recorded a video of what happens? Also, it seems that it COULD be the same issue, but it may not be, I'm not completely sure as of yet. Something I do notice, is that when using ALSA drivers (common with Kubuntu) it seems like the sound stutters, then this happens. Which is the reason why I'm trying to make pulseaudio work to test it out, but pulseaudio doesn't want to work..

---

### Post by James78 on 2009-05-24
Changed configuration to tsched=1, seems to be fine now, regardless of messages saying increasing watermark wakeup.

---

### Post by SnapeN on 2013-04-21
how do i change the configuration ?

---

