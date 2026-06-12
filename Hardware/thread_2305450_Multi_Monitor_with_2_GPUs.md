---
title: "Multi Monitor with 2 GPUs"
date: 2015-12-06
forum: Hardware
---

### Post by lwfx on 2015-12-06
I've mostly been a single GPU guy my whole Linux life and Tri-monitors was pretty easy to set up. Quad monitors had some problems but worked. Basically I'm broke and want to sell my R9 290. I have a 5450, so if I bought another 5450, do you think it would be too much of a pain in the ass to get Quad going on it? Just have never done it before and have no clue what the requirements are or how it works, and my brain is thinking it's going to be a PITA...is it a hassle?

Edit: Also, I like using the open source drivers.

---

### Post by T.J. on 2015-12-06
Not extremely difficult, no.  You just have to do a little work to configure X11 manually.  I don't have a sample handy, but I have used two cards before. You just need to specify the which driver for each of the cards via their PCI bus ID, and then configure the Screen section for positioning.  If you are extremely lazy, you could let X11 try to autodetect all cards and displays, and then manipulate them via xrandr. Ex.  xrandr --auto --output DVI-0  --right-of DVI-1

The manual setup works every time, even on older software that does not have a clue about dual/quad setups. That is not a criticism of X11.  Windows is just as bad or worse when handling two cards with independent displays.  Been there, done that.

---

### Post by lwfx on 2015-12-06
Ok, thanks for the info. I guess it will be a learning lesson for me.

---

### Post by T.J. on 2015-12-07
It's really not that hard.  First, get your replacement 5450 and let me know.  If we do it the lazy way with xrandr, it would probably take 30 minutes of your time.

---

### Post by jon_herr on 2015-12-15
I'm trying to do the same thing...  been able to "turn on" all four monitors but can't get anything more than a white-x on the 2nd set.

The Unity desktop doesn't extend to the new monitors?  

Hints, tips?

This is a dual boot machine and I was able to configure all four in windows....  funny thing, I used the same nvidia interface to do it.  Just worked.

I suspect it's my ignorance about x-windows.  Looks like two new screens, no desktop.

Help!

---

### Post by lwfx on 2015-12-15
Well I was just able to get my hands on a 6450. You think a 5450 ATI and a 6450 AMD will work together? I am using unity too like T.J.

I know if I was all expert at the X config, I'd probably be able to do this. Was doing some fancy stuff last year but if ya don't use it you lose it I guess and I forgot most of it.

---

### Post by jon_herr on 2015-12-20
Anyone?  I'm still looking for guidance on this setup.

---

