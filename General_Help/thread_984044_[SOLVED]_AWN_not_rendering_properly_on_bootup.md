---
title: "[SOLVED] AWN not rendering properly on bootup"
date: 2008-11-16
forum: General Help
---

### Post by Cammy on 2008-11-16
I'm running Hardy with Compiz-fusion, with and AWN and conky.  Everything was working properly until I uninstalled the repository version of conky (1.5.1) and installed the latest (1.6.1).  It seems like this shouldn't have a thing to do with AWN, but ever since the change, AWN won't render properly on boot up.  See the pic below.

It I go into system monitor and kill the process (as well as awn-applet-acti) and restart AWN, it works fine.  What gives?

btw, I'm running an NVidia GForce 6200LE with the latest driver from NVidia.

---

### Post by Cammy on 2008-11-16
Doh!  My special gift is that I can goof with something for two days and not figure it out, but the second I post for help on a forum, I figure it out 5 seconds later. :(

I had the idea that AWN was starting before Compiz (same problem I had with conky), so I took AWN out of sessions and stuck it in my conky delay-start script.  Seems to render properly now.

Now I just have to figure out what became of my compiz splash screen, which also seems to have bitten the dust. :confused:

Oh well, at least AWN's fixed, though it's a bit annoying to have to run so many things in a delay-start script.

---

### Post by loomsen on 2008-11-16
I'd suggest another dock to be honest, but anyway. What I actually want to point at, try

```

pstree -n

```
It will give you a processtree as output, sorted by PID. try --help instead of -n to get further options. Maybe this will help to sort your startup/remove unnecessary entries and so on.

---

### Post by Cammy on 2008-11-16
Hey, that's a useful command, thanks.

What other dock do you recommend?  I'm certainly not married to AWN.

---

### Post by loomsen on 2008-11-16
Well, depends. I like kiba a lot, unfortunately it's not being developed any longer. Then I finally forced myself to use cairo, and now that I have created my own theme from "scratch" I actually start enjoying it. Some good developement took place from 1.6.2.3, which is the version in the repos. if you're running amd64, try the debs in my sig...

You might, if doing so, want to run 
```

sudo apt-get build-dep cairo-dock

```
to build all dependencies. But it should work without as well.

---

### Post by Cammy on 2008-11-16
I tried Cairo before AWN, and it looked a bit rough, but I didn't know they'd updated it.  I don't run AMD64 (this is an old, old PC) but I'll look for a proper deb for my system.

Thanks.  AWN has always been a bit flaky for me, so I'm definitely open to alternatives.

---

### Post by loomsen on 2008-11-16
As I said, some nice improvements, you can always grab 32bit .deb from the official repos.
[http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=15317](http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=15317)

[Here's my very basic theme if you prefer it a lil simpler like me](http://www.mediafire.com/?imy2zgbdj9b)

Just extract to ~/.config/cairo-dock/themes/ and it should be available in cairos theme manager.

---

