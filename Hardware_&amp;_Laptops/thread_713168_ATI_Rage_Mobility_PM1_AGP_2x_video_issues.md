---
title: "ATI Rage Mobility P/M1 AGP 2x video issues"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by Jay Jay on 2008-03-02
Over the past few months I've become very comfortable and confident at using (X)ubuntu but there's a handful of issues which still plague my Linux experience and the major one is video performance. The hardware looks like It's struggling to achieve basic things which It did effortlessly under Windows.

Divx/Xvid films, DVD's and even Youtube clips contain horizontal frame tearing. All video based media and graphical functions judder slightly - like the on screen images are struggling to keep up, but get "left behind". This is especially evident during panning shots.  Divx/Xvid films have massive pixellation problems, other artefacts and look degraded in quality but when I view media formats under Windows they're clean and free from any issues. 

At one point (under Gutsy) I was able to get around this with X11(Ximage/Shm) in Mplayer and enjoy playback on a par with Windows (albeit with frame tearing):

```
mplayer -vo x11 -fs -zoom
```

However since downgrading to 7.04 this is no longer as effective.

Even the screensavers suffer from pausing, sluggish speed and jerkiness - very often in 2D sequences I can see the animation frames jerking and juddering along like that of old machines which didn't have a native hardware scroll facility: such as the Atari ST.[ I've enabled direct rendering]("http://ubuntuforums.org/showpost.php?p=4354283&postcount=26") but It hasn't made any difference. :confused:

I don't know if this makes a difference, but under *restricted drivers management* there isn't a listing for my ATI hardware.

If anyone can help me work through these problems I'd really appreciate it as this is the only factor that prevents me from ending any remaining reliance on Windows.

---

### Post by Jay Jay on 2008-03-05
Bump...

---

### Post by Jay Jay on 2008-03-10
Anyone?

---

### Post by tamulcahy on 2008-04-18
Hi Jay Jay. I am having problems with normal screen displays using lcd and ati rage mobility. This only happens on ubuntu, not on any other os. I have resorted to using fedora 8 until I find a resolution to this problem. The normal screen display is perfect on this. I wonder if there is a way to get the drivers from fedora and migrate them. :(

---

