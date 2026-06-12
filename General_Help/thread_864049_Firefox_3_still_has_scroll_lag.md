---
title: "Firefox 3 still has scroll lag"
date: 2008-07-19
forum: General Help
---

### Post by kvolden on 2008-07-19
I'm running Hardy on a laptop with an ATI Mobility Radeon X1300 graphics card, with the ATI accellerated graphics driver. I know a lot of people had problems with laggy scrolling in FF3 beta, but it seems like the release version had fixed the issue for most of them. Not for me, however. I also see the most of the people who still have the problem, and have asked on the forum, thinks turning off Compiz is a good fix, but I would like to have this problem fixed for good, as I favour Compiz over Metacity.
I'm a noob at this, so I can't do it by myself, and if you could help me, just let me know what kind of information you need. :)
The problem only exists in FF3, and switching to Metacity "solves" the problem.
Thanks in advance for any help! :)

---

### Post by spupy on 2008-07-19
Two ideas:
1. Turn off smooth scrolling:
Edit->Preferences->Advanced->General

2. If you don't want to turn off smooth scrolling, perhaps try these firefox extensions:
[https://addons.mozilla.org/en-US/firefox/addon/5846](https://addons.mozilla.org/en-US/firefox/addon/5846)
[https://addons.mozilla.org/en-US/firefox/addon/357](https://addons.mozilla.org/en-US/firefox/addon/357)

The first will work 90% I'm sure, the second is not likely to fix the issue but try it anyway.

---

### Post by kvolden on 2008-07-19
Hi, and thanks for your answer!

I've tried turning off smooth scrolling, but it's still very laggy..

---

### Post by spupy on 2008-07-19
Can you tell me what Compiz plugins have you enabled? Perhaps one of them is straining your system too much.

---

### Post by kerry_s on 2008-07-19
[http://www.ghacks.net/2008/06/28/fix-choppy-scrolling-in-firefox/](http://www.ghacks.net/2008/06/28/fix-choppy-scrolling-in-firefox/)

---

### Post by kvolden on 2008-07-20
Spupy, right now I have Desktop Cube, Rotate Cube, Animations, Window Decoration, Wobbly Windows, all in the Image Loading category, Regex Matching, and Move Window enabled. I've tried disabling all of them to see if this would have the same effect as closing Compiz completely, but it had no effect at all. Same lagging occurs. I don't think it's system strain, btw, as I'd expect to see lagging in more places than just the scroll-lag in FF, but then again, I'm a noob. :)

kerry_s, I tried both of the things in your link, both reinstalling Flash (which I didn't think was going to do any good anyway, as laggy scrolling takes place in flashless sites as well), and adding the mentioned line to userChrome.css, and none of the methods work. Thanks for your time and answer, though. :)

I've also tried to keep Compiz, but switch to GTK Window Decorator instead of Emerald, through Compiz Fusion Icon, as a means of isolating the problem somehow, but that didn't help either.

Oh, and "glxinfo | grep direct" in the terminal gives me "direct rendering: Yes". I saw somewhere that a disabled direct rendering could cause the problem, but that's not the issue in my case, as you can see.

---

