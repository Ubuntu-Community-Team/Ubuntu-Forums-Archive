---
title: "3D game with open source ATI/Radeon driver?"
date: 2009-12-11
forum: Hardware
---

### Post by olifhar on 2009-12-11
Almost a year ago, when the newest ATI Catalyst driver still had support for my notebook's Mobility Radeon X1600 (R500 chipset series), I purchased the enjoyable [Penny Arcade game Rain-Slick Precipice of Darkness Episode 2]("http://www.rainslick.com/revisions/thegame/episodetwo.htm"). [I]It ran just fine
[/I], and I got about six hours into the game before giving up games for a period of time.

Then came two changes: the announcement that ATI/AMD would drop support for my card in the next Catalyst driver release, [then a kernel and xserver update]("http://www.diigo.com/08h54") that [prevented me from using the older Catalyst 9.3 driver]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.10&lang=English").

I didn't pay close attention when that all happened. I wasn't playing very many games.

Tonight I decided to take a break and fire up the game. I got this message:
[IMG]http://farm3.static.flickr.com/2669/4178197408_2ee183ebec_o.jpg[/IMG]
[SIZE="1"][/SIZE]

I Googled the error message and found [this ]("http://forum.playgreenhouse.com/jforum/posts/list/1084.page") and several other threads. The solution for everyone seemed to be to update to the latest binary driver...

...which doesn't bode well for me, who can no longer avail of fglrx. I'm emailing Hothead support, but I'm pessimistic they have a fix beyond downgrading to 8.10 or earlier. What do you guys think in the meantime? Am I screwed?

*[SIZE="2"](I've attached what I think the the relevant lshw output. After all this time, I still haven't learnt the relevant modprobe magic spell. Heh. I'd be happy to learn, though.)[/SIZE]*

---

### Post by Yellow Pasque on 2009-12-12
> Am I screwed?At the moment, yes, unless you manage to get an older xserver and install the binary drivers.

Open source GLSL 1.2 for R300-R500 cards will likely come via a Gallium3D driver, which is under development for now: [http://cgit.freedesktop.org/mesa/mesa/tree/src/gallium/drivers/r300?id=c6b450033d7ec2a415b1d761da1d94588358c94b](http://cgit.freedesktop.org/mesa/mesa/tree/src/gallium/drivers/r300?id=c6b450033d7ec2a415b1d761da1d94588358c94b)

.. but who knows, the classic mesa driver is still being worked on too: [http://cgit.freedesktop.org/mesa/mesa/](http://cgit.freedesktop.org/mesa/mesa/)

---

### Post by olifhar on 2009-12-17
Thanks. I've learned my lesson, and in the future I'll probably avoid ATI cards completely.

---

### Post by Yellow Pasque on 2009-12-17
> **olifhar said:**
> Thanks. I've learned my lesson, and in the future I'll probably avoid ATI cards completely.

That's not the lesson; it's not that simple, but I digress...

---

