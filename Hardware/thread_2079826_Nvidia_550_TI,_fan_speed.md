---
title: "Nvidia 550 TI, fan speed"
date: 2012-11-02
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2012-11-02
regardless of the load on my GPU the fan speed stays the same
```
nvidia-smi -q | grep "Fan Speed";nvidia-smi -q -d temperature | grep Gpu
```i am trying to find out if this a a firmware bug or a driver bug (bad reporting or accurate)

---

### Post by Axxon95 on 2012-11-03
> **pqwoerituytrueiwoq said:**
> regardless of the load on my GPU the fan speed stays the same
```
nvidia-smi -q | grep "Fan Speed"
```
i am trying to find out if this a a firmware bug or a driver bug (bad reporting or accurate)

Seems like you have the same concern I had.

What about the temps?
I have a superclocked GTX 460 that stays at 30% fan speed until I get past 60c, regardless of Operating System.

---

### Post by pqwoerituytrueiwoq on 2012-11-03
idles below 30C; peaks at 55C (Unigine Heaven 3.0)
my card has a good heat sync
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121435](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121435)

---

### Post by Axxon95 on 2012-11-03
> **pqwoerituytrueiwoq said:**
> idles below 30C; peaks at 55C (Unigine Heaven 3.0)
my card has a good heat sync
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121435](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121435)

I guess what I'd suggest is trying to get it past 60c. I believe the NVIDIA hardware+bios will take over after getting to a set temp.

---

### Post by pqwoerituytrueiwoq on 2012-11-03
aside form physically blocking the fan on the GPU i don't see the temp hitting 60C

---

### Post by grantjohnston on 2013-02-09
I have a 550ti GTX as well (primary and secondary) and I have issues with the primary getting HOT (I've seen it get up to 70* for a bit) and it usually runs at 59-62* when I run in Linux (which is most of the time).

However, when I run in Windows I get no troubles with it whatsoever.

Also, as soon as I can figure out my problems attempting to get 3 monitors to run in *nix (two monitors and my TV to watch movies/TV) I won't be needing Windows anymore, so if anyone could come up with a solution to the melting hot graphics card, that would be great!

---

### Post by pqwoerituytrueiwoq on 2013-02-09
which driver, nvidia or nouveau?
what temps do you get when running heaven 3.0, how well ventilated is your card

i picked the asus one cause of the cooler on it, then waited for a sale
my system:
[http://imgur.com/gallery/BDFtX](http://imgur.com/gallery/BDFtX) you can't see the side fan for the gpu i have a 120mm fan on low there

---

