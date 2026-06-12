---
title: "Lubuntu mouse drift (or jump) on Dell laptop"
date: 2012-07-04
forum: Hardware
---

### Post by hans12345 on 2012-07-04
I have an old Dell Laptop (Latitude C610), 256 Meg RAM, 20 G HD which I want to set up for my wife to do simple stuff. It did run Win XP, but got too slow. I have 3 PCs with Ubuntu and 2 years experience

I installed 12.04 Lubuntu and it works except for a mouse (mouse and touchpad) drift problem. Drift is probably an understatement, the mouse pointer races to a corner (can be anyone) quite unpredictably. Once this happens (and sometimes it does not happen), the laptop is unusable.

Now this problem (which is in essence a HW problem linked to the touchpad) also happened some years ago when I got the Dell with Windows XP and after scanning the Net for ideas, I fixed it by loading the synaptics mouse driver (to see what the XP solution was related to, look at [http://www.synaptics.com/resources/consumer-tips](http://www.synaptics.com/resources/consumer-tips))

Scanning the forums, I find this hardware fix:
[http://gimbo.org.uk/blog/2005/11/12/fixing-mouse-drift-on-a-dell-latitude-c600-with-a-sledgehammer/](http://gimbo.org.uk/blog/2005/11/12/fixing-mouse-drift-on-a-dell-latitude-c600-with-a-sledgehammer/)

But I really want a SW fix. There are lots of old posts.

I have scanned old threads, but they carry a strong health warning about their use today.

I also found a reference to:
[http://qsynaptics.sourceforge.net/about.html](http://qsynaptics.sourceforge.net/about.html)
but the indication was that this was not a solution.

Best so far seems to be to try:
[http://ubuntuforums.org/showthread.php?t=427752](http://ubuntuforums.org/showthread.php?t=427752)
which is to change the xorg.conf file

or to try:
[http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/)
Tweaking your Synaptics Touchpad (laptops) : Ubuntu (6.06.1 / 6.10)
but this is an old post.

Questions:
1. Is there an equivalent synaptics driver for Lubuntu?
2. Should I try the ubuntuforums.org/showthread.php?t=427752
3. Should I try the 'Tweaking your Synaptics Touchpad Ubuntu 6' solution?
4. If not, any ideas how to do a SW fix for the mouse?

Your help appreciated.

---

### Post by hans12345 on 2012-07-12
Bump

---

### Post by hans12345 on 2012-07-21
Bump.

---

### Post by sudodus on 2012-07-23
Maybe your problem is that your hands activate the touchpad when you don't want it. Then you can disable it, when you use a mouse with touchpad-indicator according to this link

> **sudodus said:**
> I use touchpad-indicator in Lubuntu 12.04 and it works nicely. See this link (the link is old, but touchpad-indicator is alive and works in 12.04)

[[COLOR="Red"]_http://ubuntuguide.net/quickly-enabledisable-laptop-touchpad-with-touchpad-indicator-in-ubuntu-10-10_[/COLOR]]("http://ubuntuguide.net/quickly-enabledisable-laptop-touchpad-with-touchpad-indicator-in-ubuntu-10-10")

Another choice is to 'Disable Touchpad Click' acccording to this link

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=2030032&highlight=touchpad_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2030032&highlight=touchpad")

It might also be a hardware problem, that the mouse is bad. Test with another mouse!

---

### Post by hans12345 on 2012-07-24
Thanks Sudodus.

I rule out a mouse problem. This problem started with Win XP when I first got the laptop 5 years ago! It is a known trackpad problem with early Dells and there is a synaptics XP driver fix which I used. There is even a fix to cut the cable running to the trackpad!

I dont like cutting cables, but this software trackpad disable looks promising. I'll check it out.

---

