---
title: "Nvidia multi-monitor setup won't span screens"
date: 2013-05-26
forum: Hardware
---

### Post by skewray on 2013-05-26
I have an Nvidia GTX 680 with multiple screens using twinview.  Works great for general use. When I try using Wine, though, the window is never larger than a single screen, even if I set it larger with winecfg.  Also, programs that use full-screen will also use only one monitor, while the other goes black.  How do I make these programs truely think that my monitors are one giant screen?

Oddly, most of my web searching has found people with the opposite problem - their windows always span the screens.

---

### Post by skewray on 2013-05-30
bump

---

### Post by skewray on 2013-06-06
bump

---

### Post by skewray on 2013-06-23
bump

---

### Post by jp734 on 2013-06-23
skewray - have you figured this one out yet? I am having the same issue. I am using lubuntu 13.04, fglrx (2 radeon hd video cards), 3 monitors. Everything is working fine except wallpaper will not span as well. How's your xorg.conf? Does it have "virtual ???? ???" under screen section?

---

### Post by skewray on 2013-06-23
Nope.  The xorg.conf file is ignored, at least with the nvidia driver.  I get three copies of the wallpaper image, one per screen.  That's okay for me.  I just today started to sign up for an account at the nvidia forums, since the ubuntu forums have been useless.  Didn't used to be that way.

---

### Post by jp734 on 2013-06-24
That's strange. I know, with mine, it uses the xorg.conf file. I know this because every time i delete it, I get a cloned screen and the third monitor doesn't work. If I put it back, I get all three monitors working again. Well, will keep searching and post here if I find an answer. Good luck!

---

### Post by skewray on 2013-07-18
bump

---

