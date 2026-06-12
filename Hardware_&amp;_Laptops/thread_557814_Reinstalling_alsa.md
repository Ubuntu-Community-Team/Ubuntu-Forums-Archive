---
title: "Reinstalling alsa"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by Black Hawk on 2007-09-23
Hi. I've compiled the latest alsa-drivers from source. Now I can only use alsa sound through oss emeulation even in programs which supports alsa nativly. Why is this? 

Whell I tried reinstalling alsa from the repos like this

apt-get remove --purge alsa-base linux-sound-base alsa-utils
and then 
apt-get install alsa-base linux-sound-base alsa-utils

When I did that no soud modules got loaded.

All in all i'm not able to use alsa sound what so ever, please help.

---

