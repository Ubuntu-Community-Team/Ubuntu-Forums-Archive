---
title: "Trouble Installing Icecat"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by rdiggs on 2009-02-03
I am trying to install Icecat and have come across so many problems. Luckily, this forum is amazing and has helped me push through my inherent newb problems and get to a point I just can't figure out.

I've extracted the file and entered this:

```
rdiggs@rdiggs-laptop:~/Desktop/icecat-3.0.5-g1$ ./configure
```

After going through a lot of stuff, it finally gets to this point and I don't know what to do.

```
checking for sys/int_types.h... no
Building Python extensions using python-2.5 from /usr
configure: error: Could not compile basic X program.

```

If anyone can shed some light on this for me I would be very grateful.

---

### Post by Partyboi2 on 2009-02-03
You probably need the  libxt-dev package installed.
```
sudo apt-get install  libxt-dev 
```
Then run ./configure again.

---

