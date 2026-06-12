---
title: "Intel Graphics Driver problems..."
date: 2009-02-25
forum: Hardware
---

### Post by nixscripter on 2009-02-25
I have built-in Intel graphics in a Dell Inspiron 1420n:

```
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller
```

The 3D graphics don't really work. Trying to play 3D games under wine, for example, result in a crash inside the driver code.

My question is simple: will using a newer version of the Intel drivers than in the Gutsy repository work? According to their website, version 2.6.0 was just released. Has anyone tried it?

---

### Post by nixscripter on 2009-02-26
Well, looking at it, there is a new version from the Intel site. I'm on Gutsy, so I'm stuck at version 2.2 (Ubuntu-specific), and the 2.4.0 release notes claims to fix problems.

I'll try building a package manually and let everyone know how it works.

---

### Post by nixscripter on 2009-02-26
Okay, I got it working -- barely.

The problem is the version I compiled is 100,000 times slower. Compiz desktop cube spins at about two frames a second, whereas before, it was fine.

Is there a way to know how Ubuntu compiled their binary drivers to know what I'm doing wrong?

---

### Post by nixscripter on 2009-03-03
I repeat my question more specifically: what build process does Ubuntu use for their drivers? The simple

```
tar xvf xf86-video-intel-2.4.0.tar.gz
cd xf86-video-intel-2.4.0
./configure
make
make install

```

seems to make all the right files, but they run really slowly.

---

### Post by nixscripter on 2009-03-11
Alright, an update.

I upgraded to Ibex, where the driver is version 2:2.4.1-1ubuntu10.3, and it works -- sort of. Now when I run 3-D applications, the rest of my screen has junk around the corners, and it locks up frequently (nothing in Xorg logs that I can see, because it's a hard lock).

Perhaps I should post a new thread, but what sort of debugging information would be useful for this new problem? Should I file a bug?

---

### Post by llib1234 on 2009-03-13
According to other people in the forum, all Intel graphic drivers are getting worse now in terms of performance. They changed the driver code significantly, and Jaunty will ship with these new drivers. I'm on Alpha 6 of 9.04 Jaunty and the desktop interface and videos are very sluggish compared to 8.04 Hardy.

---

