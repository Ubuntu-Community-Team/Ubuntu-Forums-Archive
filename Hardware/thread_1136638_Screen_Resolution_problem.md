---
title: "Screen Resolution problem"
date: 2009-04-25
forum: Hardware
---

### Post by regevs on 2009-04-25
Hello,

I am using Lenovo 3000 C200 laptop, with Ubuntu 9.04 (as of last night). . My problem is that the screen resolutions I can get are not large enough and are less than what I could get in XP. I would like to work with a larger resolution.

It should be said that: A) I already tried some things about editing xorg.conf and such, so the situation may (?) be a bit more complicated; and B) I am a complete linux novice so I would be really grateful if something could walk me through this.

(I am not sure if this is the correct forum for this - if it's not please direct me elsewhere)

Thanks a lot.

---

### Post by KhurramM on 2009-04-26
You can do:

System > Preferences > Screen Resolution

OR ........ You can try:

xrandr -q
to see what resolutions are supported for you system

then use AT YOUR OWN RISK

man xrandr

like:

xrandr -s XxY -r FPS

where
X is horizontal res
y is vertical res
FPS is refresh rate

Hope this solves your problem

---

### Post by regevs on 2009-04-26
Thanks, KhurramM.

I already tried System > Preferences > Screen Resolution, and the problem is that the resolutions that are offered to me are limited. Specifically, when I used XP I was able to use 1600x1200, which now I cannot.

Using xrandr -q didn't help, because the supported resolutions also did not include 1600x1200.

So maybe the problem is elsewhere...

Thanks

---

### Post by Hyper Tails on 2009-04-26
I have the same problem too with my desktop and it has an ati readon hd 3600 and I can only get 1400X1050 (in jaunty) and on my vista partition i can get 1600X1200

I use to be able to get 1600X1200 back in hardy and Intrepid (i could in intrepid when i installed my driver)

and when I install my driver in Jaunty i can't get to be that high

Desktop :custom built

---

### Post by KhurramM on 2009-04-28
Maybe this helps

[https://wiki.ubuntu.com/X/](https://wiki.ubuntu.com/X/)

Also I tried that I copied a working xorg.conf file of the live user into hardy and it works for me.

Hope this resolves your issues, Insha-Allah.

Adios

---

