---
title: "Video as your background or an animated background?"
date: 2008-09-23
forum: General Help
---

### Post by DarK420 on 2008-09-23
Ive seen the matrix theme
i dont want that though
i want to be able to have icons and what not

is it possible to get videos or animated pics as your desktop BG?
and if it is how do you do it?

---

### Post by nkri on 2008-09-23
You could try xwinwrap ([_link_]("http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/")), which works very well for this, but you lose your desktop icons:(  I don't think there is another way to do this, but I'm not 100% sure.

Good luck!
-nkri

---

### Post by DarK420 on 2008-09-23
> **DarK420 said:**
> Ive seen the matrix theme
i dont want that though
i want to be able to have icons and what not

is it possible to get videos or animated pics as your desktop BG?
and if it is how do you do it?

Thanks

[http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/](http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/)

This video has animation + icons?

---

### Post by DarK420 on 2008-09-24
> **DarK420 said:**
> Thanks

[http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/](http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/)

This video has animation + icons?

up

---

### Post by DarK420 on 2008-09-24
> **DarK420 said:**
> up

=/

---

### Post by loomsen on 2008-09-24
You wont necessarily lose your desktop icons.

I had matrix screensaver running on top of my desktop, tho at a high opacity level, which, imho it is very suitable for. So, the only thing happening is your wallpaper to darken a little as long as it is running.
So, I just ran it as a thin opaque layer on top of my desktop, integrated very well, I've been able to access my desktop icons back then, and it even integrated very well with conky. Just give sth like this a try:

```

nice -n 15 ./xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -root -window-id WID

```

and enjoy :)

*edit* 
some explains:
nice -n 15 --> makes xwinwrap being nice to every other application, so if another application happens to run out of mem/cpu xwinwrap wont force the screensaver/video to keep going, so no need to worry about unstable systems or high sys load or sth. I used to run glmatrix for like two weeks, got "Crazy" - by Gnarles Barkley running on one of my desktops right now. Just give it a try, toy around, and you'll find some setups you'll like, I'm sure.

ni = no input, -o 0.20 = opacity lvl (where 0 is completely transparent), fs=fullscrn, s=sticky(optionally to have it running on every viewport,
st/sp=skip taskbar/pager, b=below, nf=no focus

xwinwrap --help for available opportunities.

---

