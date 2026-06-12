---
title: "nForce Audio Drivers"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by OlineSixtyOne on 2006-01-19
I installed them (nForce 4 Ultra motherboard) and I still can't get SPDIF working. Can anyone help me get it working, because my analog outputs have a lot of static. I have tried every method I could find by searching to get it too work and it still doesn't work.

I think the problem is the drivers aren't loading. The Nvidia documentationg specifies the modification of config files that do not exist in Ubuntu. Does anyone know how to do this?

---

### Post by Virogenesis on 2006-01-20
The config used are either /etc/asound.conf or $HOME/.asoundrc 

/etc/asound.conf = system setting 
$HOME/.asoundrc will only apply to one user 

check out this link it might be able to help you 

[http://www.nforcershq.com/forum/nforce-linux-vf29.html](http://www.nforcershq.com/forum/nforce-linux-vf29.html)

---

### Post by OlineSixtyOne on 2006-01-20
Neither of those files exist on my system, so how can I stop it from loading the default drivers once I install the nForce audio?

There isn't anything that helps me install the nForce audio drivers on Ubuntu or even Debian.

Thanks for posting tho.

---

### Post by Virogenesis on 2006-01-20
Don't install the nvidia drivers they suck they are based on OSS which won't allow you to play more than one thing.
The chipset on the nforce boards i think you'll find are intel chipsets meaning you can just make a file like i suggested before and make up a config file for yourself.
But yeah you won't find either file on your system as you have to make them which is why I pointed you to that site.
hope this helps you a bit

---

### Post by OlineSixtyOne on 2006-01-21
Okay, thanks for helping. I'll work on that file tomorrow and post the results.

---

### Post by OlineSixtyOne on 2006-01-23
Tried several .asoundrc configs found there, and all I've discovered is that most of them make digital and analog outputs not work, so there is not sound whatsoever. Does anyone have a .asoundrc config that works with spdif on nforce4 motherboards.

---

