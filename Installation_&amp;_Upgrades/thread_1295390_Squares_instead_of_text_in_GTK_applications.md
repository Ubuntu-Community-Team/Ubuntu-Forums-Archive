---
title: "Squares instead of text in GTK applications"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by R33D3M33R on 2009-10-19
I've been trying to install the GUI for phoronix test suite, but something went wrong. Im using Kubuntu 8.04 and to run the GUI I had to install php-gtk. Because I didn't find one in the repos, I downloaded the source and tried to compile it. It had some missing dependencies, so I compiled glib-2.22.2, installed it and did the same with gtk+-2.18.0. The dependencies were still missing, so I compiled and installed pango 1.21.5 and then I gave up.

After restart I noticed that instead of text, there are squares in all gtk applications. I tried to do reinstall of all packages I manually compiled, but with no succes.

What now? Must I reinstall the whole system. I'm using several important gtk apps (GIMP, claws-mail etc.) and they are unusable in the current state. Screenshot attached. 
Running claws mail in console outputs this: 

```
(claws-mail:16011): Pango-WARNING **: failed to find shape engine, expect ugly output. engine-type='PangoRenderFc', script='latin'

(claws-mail:16011): Pango-WARNING **: failed to find shape engine, expect ugly output. engine-type='PangoRenderFc', script='common'

```

---

### Post by R33D3M33R on 2009-10-22
bump

---

### Post by R33D3M33R on 2009-10-27
Well I've upgraded from 8.04 to 9.10 directly but with no success. I guess I'll have to do a fresh install. Lesson learned: don't compile critical packages ;)

---

