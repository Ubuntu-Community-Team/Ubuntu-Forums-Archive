---
title: "Playing DVD's on Ubuntu."
date: 2009-09-27
forum: Indiana - US
---

### Post by Rallaster on 2009-09-27
So I loaded up Ubuntu 32-bit Jaunty on my dad's spare desktop and it's not letting him watch DVD's on it.  Totem, VLC and even RealPlayer11 is telling him that they aren't able to read the content of the disc.  :confused:

I'm running 64-bit Jaunty on my laptop and can play older DVD's on Totem, but not newer ones.  VLC is tells me it can't read either, and RealPlayer isn't available in 64-bit architecture.  

Any and all help would be greatly appreciated.  While not being able to play DVD's isn't a deal breaker for me, it is for my dad on whether or not he keeps running Ubuntu.  He's prepared to run back to Windblows if I can't get it figured out, and I don't have an answer for him.  

Please help me help him so he can truly enjoy running a great OS as much as I do.

---

### Post by yabbadabbadont on 2009-09-27
Have you seen the following help article?

[https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)

---

### Post by oboedad55 on 2009-09-28
> **Rallaster said:**
> So I loaded up Ubuntu 32-bit Jaunty on my dad's spare desktop and it's not letting him watch DVD's on it.  Totem, VLC and even RealPlayer11 is telling him that they aren't able to read the content of the disc.  :confused:

I'm running 64-bit Jaunty on my laptop and can play older DVD's on Totem, but not newer ones.  VLC is tells me it can't read either, and RealPlayer isn't available in 64-bit architecture.  

Any and all help would be greatly appreciated.  While not being able to play DVD's isn't a deal breaker for me, it is for my dad on whether or not he keeps running Ubuntu.  He's prepared to run back to Windblows if I can't get it figured out, and I don't have an answer for him.  

Please help me help him so he can truly enjoy running a great OS as much as I do.

In "Add/Remove Programs" search all programs for "restricted extras". Install them and that should do it.

---

### Post by Rallaster on 2009-09-28
> **yabbadabbadont said:**
> Have you seen the following help article?

[https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)


```

sudo /usr/share/doc/libdvdread4/install-css.sh
```Apparently that's what I was missing, I will check on my dad's comp and see what happens.

---

### Post by A.Zan on 2011-02-20
> **yabbadabbadont said:**
> Have you seen the following help article?

[https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)


I need this info but the link is broken :(

---

### Post by schultmc on 2011-02-21
> **A.Zan said:**
> I need this info but the link is broken :(

Try [https://help.ubuntu.com/10.10/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/10.10/musicvideophotos/C/video-dvd.html)

---

