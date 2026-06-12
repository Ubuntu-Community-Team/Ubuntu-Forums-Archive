---
title: "xrandr not working"
date: 2010-04-30
forum: Hardware
---

### Post by JKoder on 2010-04-30
Hello everyone !
I have a few questions for you.
I have tried xrandr tool to get some output on my tv via S-video.
My video card is ATI Radeon Xpress 1100 and i am using the opensource drivers only 

in a console i have typed:
```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
```

The screen on my laptop did flicker a little bit but nothing on TV.
I need to mention that i have tried exactly the same on openSuse M5 and it worked like a charm.

The xrandr is the same version 1.3.2

Am i doing something wrong on ubuntu ? or maybe i am missing something ?
If any of you know please help me out a little .

Big thanks !

---

### Post by conradin on 2010-04-30
I find that Xrandr has some sort of memory limitation, (apparently).
You might consider the graphical fronted Arandr, its a little easier to set up and use. 

Is your TV detected as a display?

Also, how old is your TV? I have had issues where The TV simply wouldnt cooperate with my computer hardware. (Even though it had S-video in), that, or the image quality would be all messed up.

---

### Post by JKoder on 2010-04-30
> **conradin said:**
> I find that Xrandr has some sort of memory limitation, (apparently).
You might consider the graphical fronted Arandr, its a little easier to set up and use. 

Is your TV detected as a display?

Also, how old is your TV? I have had issues where The TV simply wouldnt cooperate with my computer hardware. (Even though it had S-video in), that, or the image quality would be all messed up.

I have tried arandr as well but no result. I am not afraid to use the command line.
My tv is not that old 2 years i think. But this cannot be a reson since it does work in opensuse ( i did not tried any other distro )
I want to switch to linux completely but i need the output to svideo. May be the video drivers are somehow buggy ?

---

### Post by conradin on 2010-05-02
Yeah, I was having problems in Karmic, that were magically solved when I upgraded to Lucid. Sorry, I cant offer more help.

---

