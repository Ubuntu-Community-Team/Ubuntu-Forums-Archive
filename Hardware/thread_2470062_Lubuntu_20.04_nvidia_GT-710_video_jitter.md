---
title: "Lubuntu 20.04 nvidia GT-710 video jitter"
date: 2021-12-19
forum: Hardware
---

### Post by gdesilva on 2021-12-19
Hi,

I have been using this old PC with Pentium Duo chip running nvidia gt-710 successfully. Recently, I noted that the nvidia driver was updated to 470.86 version and since then I am experiencing constant video jitter (runs smoothly for a couple of seconds, stops for a second and starts again). 

I have been running vlc and tested it with a 4K test video and it worked reasonably well until this update. I tried out many tweaks on vlc, like increasing the disk caching and network caching but nothing seems to work. When I initially ran glxgears I got a very low fps rate (around 40) and I could see the jitter in the glxgears display but I managed to fix it by turning off vertical sync and now glxgears gives me around 2700 fps. Still I have the jitter issue in vlc.

Appreciate if anyone can make a suggestion.

Thanks

---

### Post by guiverc on 2021-12-19
You didn't specify if you're using the GA or HWE kernel stack.

GA is the *general* kernel (note: it's not *generic* as that's a different thing, and is 5.4 for the life of Ubuntu 20.04 LTS, and is default is Lubuntu 20.04 or 20.04.1 media was used for installs.

The HWE or *hardware* *enablement *kernel changes during the first ~2.5 years of the product, as is default for installs of Lubuntu 20.04.2 LTS or later (ie. it's the media used to install that dictates the default kernel).  At 20.04.2 it used the 5.8 kernel (from 20.10), at 20.04.3 it's the 5.11 (from 21.04), it'll use the 5.13 kernel at 20.04.4 (from 21.10) etc.

You can use 

```
uname -r
```

to look at which kernel you're using, and you may find just switching to the other stack is an easy fix.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

(*how to read the page varies on what kernel stack you're using; Ubuntu Desktop 20.04 LTS defaults to HWE for all media unlike Lubuntu. If you're using the HWE stack the page will match switching stack, but on most hardware you can easily have both installed, and only remove the other if you're short of disk space, want to save bandwidth on updates (both will get upgrades/fixes) or anytime you're happy*)

I don't know if this will help, but as it's usually a easy thing to try, it's why I offer it.

---

### Post by gdesilva on 2021-12-19
@guiverc,

Thanks for the response and very useful information which I wasn't quite aware of and something I will keep in mind. I am running 5.4.0-91-generic

I did manage to resolve the jitter issue by removing the CPU cooler, cleaning and applying new thermal paste. Now no noticeable jitter exists. I remembered that this was an issue some years ago and thought of trying it out!

Thanks again.

---

