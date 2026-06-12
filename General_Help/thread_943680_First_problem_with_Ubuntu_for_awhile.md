---
title: "First problem with Ubuntu for awhile"
date: 2008-10-10
forum: General Help
---

### Post by Twitch6000 on 2008-10-10
Ok so after getting this new Laptop I wanted to install ubuntu 8.10 beta onto it.

I did just that and well it seems to detect my wireless and such(atheros :O) and does everything fine except it doesn't start the x server :(.

How can I solve this problem?

My graphics card is a nvidia 8200m(I did hear the beta is having trouble with these).

So should I just try my custom hardy or wait wait for 8.10 final.

I don't know maybe you got a better idea :).

I am still shocked it is working with my wireless card out of the box >.>.

On my old laptop gusty didn't even do that nor did PClinuxOS <.<.(I am speaking about when I first got it ofcourse)

---

### Post by geirha on 2008-10-10
[This](http://en.wikipedia.org/wiki/Atheros) might explain why your atheros card is working out of the box in the beta.
> In the free software community, Atheros has been known for not releasing appropriate documentation that would allow free software developers to write open-source drivers to support their wireless devices without reverse-engineering,[3] thus OSS support for Atheros hardware was rather limited. [...snip...]
Recently, Atheros decided to change policy and released an open source Linux driver for their 802.11n devices.[7]. Atheros also released some source from their binary HAL under ISC license to help community add support for their abg chips, it can be downloaded from [http://www.kernel.org/pub/linux/kernel/people/mcgrof/legacy-hal.tar.bz2](http://www.kernel.org/pub/linux/kernel/people/mcgrof/legacy-hal.tar.bz2)


For your other question, I would stick with Hardy until Intrepid is realeased, but if you want to improve the chances that it will work well with your graphics card, go report the problem at [launchpad](launchpad.net), to help the developers with getting the information they need to fix it. You should be able to do the necessary testing using the cds live session.

---

