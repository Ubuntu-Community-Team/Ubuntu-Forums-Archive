---
title: "How to map Fn keys to use xbacklight to change backlight brightness"
date: 2009-08-31
forum: Hardware
---

### Post by hammeraxe on 2009-08-31
I tried to be as explanatory in the title as possible. I have an Acer Aspire 3810T-354G32n running Ubuntu 9.04 64bit.

Almost everything works right (except for suspend, but lets leave that for a separate thread), but I would like to improve performance of the brightness keys. They do work, but the change between brightness levels is somewhat flickery and the brightness indicator bar in the top right corner shows complete nonsense (the scale is wrong).

How would I go about fixing this?

My idea was to use scripts that run xbacklight to change the brightness by some increment, say 5 or 10 %, because xbacklight from cli works nice. Is it possible to map the Fn+Right and Fn+Left key combinations to trigger the scripts? I tried xev and xmodmap, but didnt succeed.

---

### Post by ganuro on 2009-11-02
Try using compiz. In compizconfig use commands to set that actions. In my case I use the windows key instead of Fn because it doesn't work

---

