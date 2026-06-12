---
title: "Running compiz on only one xserver"
date: 2008-08-13
forum: General Help
---

### Post by han555 on 2008-08-13
I have two xservers running and want to run compiz on only one of them because it is very slow otherwise.  If I try to disable compiz on one, it disables it on both.  Is there a way to only run compiz on a single xserver and run metacity on the other?

---

### Post by han555 on 2008-08-14
Is there a config file where I can define which window manager runs on each xserver?

---

### Post by han555 on 2008-08-18
Does anybody have any insight into this?  I just want to run one xserver with compiz and another without.  Hasn't anybody attempted this before?  With compiz running so slow when two xservers are running, it seems like this would be a pretty common setup.  Anybody?

---

### Post by han555 on 2008-08-22
Here's what I did in case anybody needs help with this in the future.

In /usr/bin/compiz, i added  --only-current-screen to the COMPIZ_OPTIONS string.  This lets me start off with only my desktop xserver running compiz.  however, this left my second xserver with no window manager apparently.  I tried loading compiz on the second xserver with "DISPLAY=:0.1 compiz --only-current-screen &" and to my surprise, both screens worked with no lag whatsoever.  I was under the impression that running compiz on 2 xservers was what was causing the slowdown, but apparently it's not that cut and dry.  Either way, my quick fix is to just run a script to start compiz on the second x server after /usr/bin/compiz.  This works fine but is not really an ideal fix.  If anybody has a better suggestion, I'm all ears.

---

