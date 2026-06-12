---
title: "ATI Dual Monitor Help"
date: 2010-07-29
forum: Hardware
---

### Post by omario on 2010-07-29
I am trying to get dual monitors to work on 10.04 (32-bit) along with Compiz (to use stuff like Docky). When the monitors are set to mirror each other, everything works great, advanced effects and everything are there. Switching to extended desktops through Monitors seems to break this (Docky notifies me that I need to enable the compiz stuff again).

My video card is an ATI Radeon 9550 (256MB), and my system is a Pentium 4 with 2.5GB of RAM. On a single monitor, everything works perfectly.

I was wondering if anybody could walk me through how to get both to work? It's the only thing keeping me from removing Windows in its entirety. Or if somebody could tell me this is not possible yet, at least I'll have the comfort of knowing it is not.

For the record, I have done my Googling and searching of these forums. I've come across some threads that have said it is not possible, a couple that have suggested things, which were entirely too complicated for me to understand what I was doing (therefore I did not try). I understand that ATI has stopped supporting this video card, and that driver used in 10.04 is an open-source driver. I understand there are limitations behind this, but from my reading, some people may have had success previously (though I'm not sure which video card/solution they used), and I was hoping maybe it would be possible for me to have success as well.

---

### Post by Yellow Pasque on 2010-07-29
When you use extended desktop, you're limited to 2048x2048. If you exceed 2048 (pixels) either vertically or horizontally, then you lose direct rendering, so no 3D acceleration, no compiz, etc. A nice illustration: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#the_Virtual_screen](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#the_Virtual_screen)

So, basically, you'll want to work on making an xorg.conf that extends your desktop vertically rather than horizontally (if your panels are still <=2048 when combined vertically).

Connect your monitors, restart X and post /var/log/Xorg.0.log if you need help.

---

### Post by omario on 2010-07-29
Thanks for your quick reply.

My monitors run at a native resolution of 1280x1024, so if I stack them vertically, it will be 1280x2048, which would then fit in the restrictions.

I will try this when I get back home and post back.

Thanks again.

---

