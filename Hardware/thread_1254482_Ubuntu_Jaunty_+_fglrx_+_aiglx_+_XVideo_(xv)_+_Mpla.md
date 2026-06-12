---
title: "Ubuntu Jaunty + fglrx + aiglx + XVideo (xv) + Mplayer"
date: 2009-08-31
forum: Hardware
---

### Post by SoulSlave on 2009-08-31
Ok, so the situation is this, following [this]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide") guide I installed fglrx quite nicely in Ubuntu 9.04, only differences being that I used the driver from ubuntu repositories (that nice little icon in the taskbar)then I enabled both AIGLX and composite, and compiz. Its working quite ok (not as smooth as nvidia, but good enough).

Problem is, when I try to use Mplayer + Xv, and try to go into full screen my system completely hangs, but when I try to use openGL movie goes pretty fine (speed wise in both windowed and fullscreen) however when i'm in windowed mode the movie keeps blinking.

Both xvideo and opengl modes are pretty fast, opengl uses some more cpu cycles, but that's ok, as I don't run many cpu intensive programs (unfortunately windows is still my gaming OS).

How could I solve this situation?

---

### Post by SoulSlave on 2009-08-31
Forgot to mention that I'm currently using texturedvideo option in my xorg.conf

---

### Post by 00arthuryu on 2009-08-31
ATI's fglrx drivers still has problems with watching videos when running compiz.
If you're compiling mplayer then i suggest you compile mplayer with a compiz patch.

[http://smspillaz.wordpress.com/2007/10/18/unlocking-the-full-video-potential-of-your-video-card/](http://smspillaz.wordpress.com/2007/10/18/unlocking-the-full-video-potential-of-your-video-card/)

It tends to make it alot faster and irons out alot of problems, but will make the video pause when you spin the cube whilst running a fullscreen video. (which is kinda annoying

---

### Post by cos85 on 2009-08-31
I have the same problem in 8.10.
I've looked far and wide, but there appears to be no solution. 

This may be of interest:
[http://brainstorm.ubuntu.com/idea/2876/](http://brainstorm.ubuntu.com/idea/2876/)

---

### Post by 00arthuryu on 2009-08-31
i'm running the same setup, and xv works.
The default 8.04 ATI drivers are out of date,
Install the latest ATI fglrx drivers from

[http://ati.amd.com/support/driver.HTML](http://ati.amd.com/support/driver.HTML)

---

### Post by SoulSlave on 2009-08-31
Acctualy I'm using 9.04 but I got the point, so, if I'm compiling MPlayer would I still be able to use gnome-mplayer? 

Plus I've heard that opengloverlay optin in xorg.conf would solve this issue with my video blinking when playing with opengl enabled?

Could anyone confirm this?

---

