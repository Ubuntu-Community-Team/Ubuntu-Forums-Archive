---
title: "Display COMPLETELY messed up! Coloured pixels at top of black screen"
date: 2010-07-21
forum: Hardware
---

### Post by H4rm0ny on 2010-07-21
I had until yesterday a working Kubuntu install. Today, booting up results in little more on the screen than a few rows of coloured pixels. Get this - it's not just when kdm starts up. Even if I tell it to boot up directly to command line, the same happens.

Now aside from the display issue, things appear to be running. I haven't actually logged in to the box from another machine, but I suspect it would be fine. Num Lock goes on off, etc. I have two other OS/s on the same machine - an old Windows XP and a recent reinstall of Gentoo. Both work fine. I've made no changes recently that I can think of, not fiddled with the system in any significant way. It's possible some update came down the line and I installed it faithfully as usual - I don't recall such but it's quite possible. The only significant thing I did was set up Xorg on my Gentoo OS which is on a completely different partition and can't even mount the / partition for my Ubuntu one as that's ext4 and I forgot to compile support for that into my kernel ( "doh!" ). So I can't see any way the other OS/s could have interefered, but I mention it for completeness because it's all I can think of.

Can anybody help me with this? My next recourse is to reinstall Kubuntu. Not as painful as it might be as my /home is on a separate partition, but I'll still have to go through two weeks of realising I haven't reinstalled something yet. Also, I'd really like to know what's causing it!

I've had a look through the logs for dmesg and Xorg, but I can't see anything significant and don't really know what I'm looking for.

Anyone suggest what this could be or how to begin investigating?

Hardware is Asus Motherboard (I'd need to look up the model), AMD Phenom II X2, HD4830 graphics card.

Thanks for any help,

H.

EDIT: OS is Lucid Lynx.

---

### Post by PresenceofMind on 2010-07-21
Hello there!

Are you confirming that these symptoms only occur in Kubuntu and not in any other OSs you have installed? 

If that's the case, then I think it's safe to assume that the drivers are behind this. The pixel lines are the sign that your GPU driver is not functioning at its best. With the ATi Catalyst drivers, it's a case of hit or miss....

Someone correct me if I'm wrong.

---

