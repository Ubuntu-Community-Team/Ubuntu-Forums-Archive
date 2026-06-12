---
title: "Random crashes and OpenGL instability (nvidia)."
date: 2006-09-29
forum: Hardware &amp; Laptops
---

### Post by phibxr on 2006-09-29
I'm having serious problems with running Ubuntu on my HP Pavilion 3410. This is the relevant hardware:

CPU: AMD Athlon 64 3600+ 2,4GHz
RAM: 512MB
GFX: Geforce 7300le

If I leave the computer on for a long time (i.e. when I go to sleep) with no screensaver activated, it might just hard freeze even though no applications save for GDM are running.

This is my last entries in /var/log/messages for tonight when this happened:

```
Sep 29 03:31:21 ubuntu -- MARK --
Sep 29 03:51:22 ubuntu -- MARK --
Sep 29 04:11:22 ubuntu -- MARK --
```

Also, when I use applications that uses OpenGL, it either locks up at once (in games, the graphics freeze and the sound starts repeating) or after a while (I was able to keep Enemy Territory alive for a few minutes, but Planet Penguin Racer crashes as soon as I press a key to start the game).

This may be worth to mention; I've tried both Windows Vista and Windows XP, and in neither do I have any of these problems no matter how long the computer is running or whether I'm using OpenGL or not. My temperatures are okay and my install is clean.

I'm using Dapper 6.06 32 bit fully upgraded with the k7-kernel (i've tried the 686 kernel too with the same results).

---

